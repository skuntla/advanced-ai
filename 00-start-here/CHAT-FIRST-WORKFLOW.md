# Chat-first mastery workflow — curriculum learning protocol (v1)

**Status:** Agreed learning process · **Adopted:** 2026-10-24 · Applies across all **27 knowledge domains**, **14 solution families**, and **14 failure categories**.

> ChatGPT is the interactive classroom. GitHub is the verified, durable learning reference. Understanding drives progress; generating content does not establish mastery.

## Decision: chat first, not a textbook dump

1. **Publish a scoped syllabus first.** List prerequisites, ordered modules, subtopics, expected outcomes, authoritative sources, and the domain exit challenge. This is the map, **not** a claim that lessons are already complete.
2. **Teach one micro-concept at a time in conversation.** Start with a concrete problem and approachable intuition. Introduce vocabulary, internal mechanics, a small worked numerical or event-sequence example, and diagrams as needed.
3. **Invite questions and adapt.** Learner explains the idea in their own words. If there is confusion, change the analogy, reduce the numbers or draw the exact process before going on. Do not advance solely because a timer elapsed or an answer sounds fluent.
4. **Test application and changed assumptions.** One question at a time, increasing from recall to a realistic architecture decision, edge case and failure diagnosis. Explicitly distinguish facts, assumptions, uncertain outcomes and evidence.
5. **Prove important claims.** Choose an independent oracle, paper trace, toy simulation or small AI-assisted experiment. The learner predicts the expected result, checks actual output and records the difference. No production or sensitive data in labs.
6. **Check in a polished micro-lesson.** Convert verified learning into original, standalone documentation with rationale, worked example, diagram, alternative approaches, failure modes, tests and primary references. **Do not commit raw chat transcripts as lessons.** Capture unresolved questions honestly.
7. **Revisit and integrate.** Use spaced recall (1/3/7/14/30 days), link the concept to solution families/failure categories, then finish the whole domain with an unfamiliar architecture case and independent defense.

## Twelve ingredients of a complete micro-lesson

| # | Ingredient | Expected evidence |
|---|---|---|
| 1 | Prerequisites and intended outcome | What knowledge is assumed and what learner should be able to do |
| 2 | Driving question and motivation | What concrete problem exists without this technique |
| 3 | Simple intuition | Plain English, small analogy and where analogy fails |
| 4 | Technical mechanism | Accurate internal states, operations and definitions |
| 5 | Visual / numerical worked example | Reproducible values or an event-by-event sequence diagram |
| 6 | Architecture patterns | At least two meaningful alternatives and selection criteria |
| 7 | Enterprise scenario | Actors, scale, invariants, business consequences, human ownership |
| 8 | Failure modes and boundary conditions | What fails, what is unknown, containment and recovery |
| 9 | Independent validation | Oracle, checks, traces and falsification criteria |
| 10 | Adaptive questions | Recall, reasoning, design defense and changed constraint |
| 11 | Authoritative references | Link actual sources; distinguish facts from invented examples |
| 12 | Mastery and recall record | Dated evidence, unresolved misconceptions and next review |

Depth is proportional to the concept: mathematics is required where meaningful; code is a verification tool, not the primary learning objective.

## Domain lifecycle and completion rules

- **Mapped:** syllabus and chapter outline exist.
- **Learning:** micro-concept is being discussed; questions remain.
- **Explained:** learner can teach mechanism with an example without prompts.
- **Applied:** learner handles novel architecture trade-offs and failure scenarios.
- **Verified:** independent evidence, review and cold scenario defense support mastery.

Track objective proficiency using the existing **0–4 rubric** in [LEARNING-METHOD](LEARNING-METHOD.md). A status of *Learning* must not be mistaken for Level 2+ proficiency. A chapter being checked into GitHub does not mean mastered. No fabricated test passes, scores, reading completion or dates.

## Check-in cadence and quality gate

- Check in **one verified lesson per finished micro-concept** rather than deferring all writing until an entire domain is complete.
- Update domain table of contents and [PROGRESS](PROGRESS.md) only with actual study evidence.
- Clearly label illustrative simulations, assumptions, out-of-date vendor details, and unresolved design questions.
- Verify equations, event sequences, links, guarantees, threat boundaries and security assertions before calling a lesson publication-ready.
- Where strong claims are about external products, rely on primary docs/current validation, not a plausible AI explanation.
- A final domain challenge combines **relevant knowledge domains × one solution family × multiple failure categories**.

## AI-native but evidence-driven

The learner may have AI generate simulations, code, architecture diagrams, tests, and draft materials. Before code, the AI should restate goals/non-goals, identify assumptions, challenge risky design choices, propose alternatives and specify falsifiable tests. Learner owns correctness, release judgment and business impact. Prefer an economical toy experiment over a giant implementation.

## Suggested 60–90 minute format (adapt, do not enforce)

- 25–35 min: discussion and first-principles mechanism
- 15–20 min: probing questions and unfamiliar scenario
- 15–20 min: worked trace / independently verifiable experiment
- 10–15 min: explain back and challenge
- 5 min: capture notes, confusion, sources and next review

If a micro-concept takes multiple sessions, continue it rather than prematurely moving to the next topic.

## Starting point

Start [D20: Distributed systems](../01-knowledge-domains/06-distributed-infrastructure/20-distributed-systems-and-data-consistency/README.md) with the [10-module roadmap](../01-knowledge-domains/06-distributed-infrastructure/20-distributed-systems-and-data-consistency/MODULE-ROADMAP.md) and [Module 01: Fundamentals](../01-knowledge-domains/06-distributed-infrastructure/20-distributed-systems-and-data-consistency/module-01-fundamentals/README.md). As you learn, link completed modules to [LoRA](../04-worked-lessons/lora-from-first-principles.md), [RAG security](../04-worked-lessons/permission-aware-rag.md) and [unknown-outcome recovery](../04-worked-lessons/unknown-outcome-and-idempotency.md) examples when relevant.
