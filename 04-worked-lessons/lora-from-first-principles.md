# LoRA from first principles — How can a frozen model learn?

**Relevant domains:** D08, D09, D10, D24 · **Purpose:** intuitive → mathematical → training → architecture decision.

## Driving question
A model has billions of frozen weights. A bank wants to teach it to classify compliance incidents more consistently. If nothing in the original model is updated, where does learning happen?

**Answer in one sentence:** LoRA trains small, additional matrices that contribute an additive weight update to selected linear transformations; the frozen base computations remain, but their outputs are adjusted.

## 1. First understand one ordinary layer
A linear neural-network layer maps input vector `x` to an output `y = Wx`, where `W` is its weight matrix. The entries of W were learned earlier. Freezing the model means the training optimizer does **not update W**, not that its computations disappear.

For an input of 1,000 numbers and output of 1,000 numbers, W has 1,000×1,000 = **1,000,000** learned entries.

Full fine-tuning could update all one million entries of this *one* layer; multiply the scale across many layers to understand why a large model is expensive to tune.

## 2. A smaller adjustment can still alter the answer
Rather than learning a separate unrestricted 1,000×1,000 matrix ΔW, factorize the adjustment as two smaller matrices:

```text
x (1000×1) ──────────────> W (1000×1000, frozen) ──────────┐
     │                                                      │
     └──> A (10×1000, trainable) ──> B (1000×10, trainable) ─┤ add
                                                            ↓
                                                          output
```

The formula for a standard LoRA-instrumented linear layer is:

```text
y = W x + (alpha/r) B A x
              └ learned correction ┘
effective W = W + (alpha/r) B A
```

Matrix multiplication has to match dimensions: B×A is (1000×10)×(10×1000), producing a (1000×1000) correction. In actual forward computation, the system can evaluate A×x first, then B×(Ax), without explicitly building a dense correction matrix.

- W has 1,000,000 frozen weights.
- A has 10×1000 = 10,000 trainable weights.
- B has 1000×10 = 10,000 trainable weights.
- Together A+B have **20,000** trainable weights, **2%** of the original matrix's count (98% fewer for this example).
- The intermediate dimension **r = 10** is called the rank. Low rank limits the changes that can be represented; it is not arbitrary magic.

**Important caveat:** The matrix-product adjustment only covers a constrained subset of possible dense changes, and LoRA may be attached to several selected projection matrices throughout a model. Parameter savings for an entire network depend on those choices. Runtime, optimizer, activation and inference memory costs are not identical to the trainable-weight ratio.

## 3. Hand calculation with a 4×4 matrix
Imagine W is the 4×4 identity matrix. The model receives `x=[1,2,0,0]ᵀ`; frozen layer output `Wx=[1,2,0,0]ᵀ`.

Choose rank r=1, scaling alpha/r=1 and **illustrative, already learned** adapter values:

```text
A = [1  1  0  0]          dimensions 1×4
B = [1  0  0  0]ᵀ         dimensions 4×1

Ax = 1×1 + 1×2 = 3
B(Ax) = [3, 0, 0, 0]ᵀ
y = Wx + B(Ax)
  = [1,2,0,0]ᵀ + [3,0,0,0]ᵀ
  = [4,2,0,0]ᵀ
```

The original matrix W has not changed at all, but the output has. That is the core insight.

## 4. How training discovers the numbers
Your 20,000 expert-labeled incidents are **examples**, not a precomputed table of adapter weights. Training sends examples through the frozen model plus adapter, compares predictions to targets, computes a loss, backpropagates gradients through the forward path, then updates **A and B** using an optimizer.

### Tiny numerical gradient example
Let's reduce the problem to 2D purely to illustrate gradient flow. This is not a real language-model training objective.

```text
W = identity(2)
x = [1, 2]ᵀ
A = [1, 1]
B = [0, 0]ᵀ             common style of zero initial adapter contribution
target output t = [4, 2]ᵀ
scaling = 1

Ax = 3
initial y = Wx + B(Ax) = [1,2]ᵀ
squared loss L = 1/2 * ((1-4)² + (2-2)²) = 4.5
```

With this squared-loss illustration, the derivative for B is `(y - t) * (Ax)`, so `dL/dB = [-9, 0]ᵀ`. A hypothetical one-step gradient update with learning rate 1/9 gives `B_new=[1,0]ᵀ`, producing `y_new=[4,2]ᵀ`, hence loss 0 on *this one constructed case*. It says nothing about generalization.

Why can A initially remain unchanged in this example? Its gradient travels through B; when B is zero, the immediate gradient for A is zero. Once B has moved, subsequent updates can alter A too. Different practical initializations/optimizers affect the early dynamics.

**What stays frozen:** base W. **What changes:** selected adapter weights A and B. **What drives change:** gradient of a specified training loss measured against expert-labeled examples.

## 5. What 'attached to the model' actually means
Usually LoRA modifies selected linear modules (for example attention projection layers) by replacing the forward operation `Wx` with the sum `Wx + scale*B(Ax)`. Training saves only adapter parameters and configuration while the frozen base model weights remain shared. For compatible configurations, trained updates can later be merged into the base model's corresponding matrices for inference.

This does **not** mean attaching a knowledge database, dynamically retrieving documents, or simply appending extra prompt text.

## 6. Compare prompting, RAG and LoRA
| Bank requirement | First candidate | Reason |
| --- | --- | --- |
| Latest regulatory threshold changes daily | Permission-aware RAG | Source remains authoritative and frequently changes |
| Correctly classify incidents into stable custom categories | Prompt baseline → compare LoRA | Learn consistent task behavior from labeled examples |
| Fetch live trade or entitlement status | Authorized tool/API | Must read live source of truth |
| Enforce whether AI may update books | Deterministic policy + human controls | Authorization/business invariants must not depend on model confidence |
| Model's output format is inconsistent | Structured decoding/prompting before fine-tuning | Simpler fix may suffice |

A single system may use all of these mechanisms together; they solve different problems.

## 7. Failure cases a Principal Architect must anticipate
1. Labels are inconsistent between compliance experts: adapter faithfully learns noise.
2. Historical incidents leak into holdout through near-duplicates: apparent gains are fake.
3. Model becomes better on frequent classes but misses rare severe events.
4. New policy changes after fine-tuning: the adapter is not a reliable current-policy database.
5. Wrong base/adapter version pairing changes behavior.
6. Training is economical but serving or evaluation still has unacceptable cost/latency.
7. A tuned model produces confident but unsupported predictions; require evidence and review thresholds.

## 8. Verification plan
Create train/validation/test splits by incident chronology or entity when needed to prevent leakage. Compare the exact same independent holdout cases for (a) base model with prompting, (b) retrieval-enhanced baseline, (c) LoRA-adapted model, and (d) a conventional classifier if reasonable. Report per-category precision/recall, confusion matrix, cost/task and robustness to changed policy text. Define a human review path for ambiguous or high-risk classifications.

**Do not approve fine-tuning solely because training loss decreased**—that only establishes fit on training data.

## 9. Learn-it-for-real exercise
Before asking a coding agent to implement, predict the outputs in the 4×4 and 2×2 examples above. Then have AI write a *minimal* Python/PyTorch illustration showing W frozen, gradients/updates on A and B, and different outputs before and after optimization. Check parameter counts and gradients independently.

**Cold interview questions:** Why multiply A and B instead of learning ΔW directly? What does rank change? How does training still have gradients if W is frozen? When is LoRA the wrong answer? What result would disprove the LoRA business case?

## References
- [Original LoRA paper](https://arxiv.org/abs/2106.09685)
- [Hugging Face PEFT LoRA conceptual guide](https://huggingface.co/docs/peft/main/en/conceptual_guides/lora)
- [Sebastian Raschka — LoRA/DoRA from scratch](https://magazine.sebastianraschka.com/p/lora-and-dora-from-scratch)

*All numeric values above are constructed teaching examples, not benchmarked empirical results.*
