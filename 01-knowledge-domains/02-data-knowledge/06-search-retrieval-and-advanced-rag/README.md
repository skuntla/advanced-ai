# Domain 06 — Search, retrieval and advanced RAG

> Pillar 2: Enterprise Data and Knowledge Systems · Status: **curriculum chapter / guided study** · Depth target: explain → design → challenge → prove.

## Why this matters
Turn heterogeneous and changing enterprise data into trustworthy, authorized context. In this domain, the architect needs more than terminology: they must choose an approach, specify its guarantees, and defend its limits.

## Learning outcomes
After studying this domain you should be able to:
1. Explain every essential mechanism below in plain English and at implementation depth.
2. Draw a production-grade design with trust boundaries, dependencies and failure states.
3. Identify non-obvious assumptions; compare alternatives based on business risk.
4. Use AI coding agents to prototype experiments, then independently verify outcomes.
5. Answer the scenario questions cold, without relying on AI-generated answers.

## Detailed concept checklist
1. **Embeddings** — define it; explain the internals; when to use it; where it fails; how to verify it.
2. **cosine similarity** — define it; explain the internals; when to use it; where it fails; how to verify it.
3. **BM25** — define it; explain the internals; when to use it; where it fails; how to verify it.
4. **HNSW/ANN** — define it; explain the internals; when to use it; where it fails; how to verify it.
5. **hybrid search** — define it; explain the internals; when to use it; where it fails; how to verify it.
6. **reranking** — define it; explain the internals; when to use it; where it fails; how to verify it.
7. **metadata filters** — define it; explain the internals; when to use it; where it fails; how to verify it.
8. **query decomposition** — define it; explain the internals; when to use it; where it fails; how to verify it.
9. **multi-hop search** — define it; explain the internals; when to use it; where it fails; how to verify it.
10. **citation grounding** — define it; explain the internals; when to use it; where it fails; how to verify it.
11. **retrieval evals** — define it; explain the internals; when to use it; where it fails; how to verify it.

## Walkthrough scenario
**Problem:** For settlement code SETT-0942, compare exact-code keyword retrieval with semantic policy questions and hybrid ranking.

**How to reason about it:**
1. Identify the authoritative business facts, risk boundaries, actors and measurable success.
2. Separate **facts**, **assumptions**, **model inferences**, and **decisions**; obtain independent evidence.
3. Draw the minimal flow from input through state, data/tools, decision and output/action.
4. Define both happy path and failure path, including visibility, retry/recovery and human escalation.
5. Define tests and release criteria before authorizing AI-assisted implementation.

**Architectural trade-off:** Balance prefilter security, top-k recall, index cost and latency; retrieval candidates are not inherently authorized.

## Failure laboratory
Investigate each of these as a reproducible failure hypothesis:
1. Correct source not found. Record the trigger, blast radius, evidence, containment, durable fix and regression test.
2. restricted chunk retrieved. Record the trigger, blast radius, evidence, containment, durable fix and regression test.
3. stale policy ranks first.. Record the trigger, blast radius, evidence, containment, durable fix and regression test.

## Decision and review questions
- Why can high similarity be a poor answer?
- How would you separate retrieval from generation errors?
- What would change your design if the organization forbade sensitive data leaving its network?
- What concrete evidence would convince security, operations and the business owner to approve it?

## AI-assisted verification exercise
Give a coding agent the *scenario* and ask it to propose three designs, their assumptions and likely failures **without coding yet**. Challenge its reasoning. Approve only a small, isolated prototype that simulates one high-risk failure. Predict the outcome before running it; collect traces, compare against an independent oracle and document any surprising behavior.

## Learning artifacts to produce
- One-page mental model with a small numerical or workflow example.
- Annotated component and sequence diagrams; trust boundaries included.
- Trade-off/ADR and failure-mode table.
- Executable micro-experiment or independently checked worked case.
- Five recall questions, three architectural decisions, one adversarial scenario.

## References (read in order)
- [Primary reference](https://learn.microsoft.com/en-us/azure/search/hybrid-search-overview)
- [Pillar reference](https://learn.microsoft.com/en-us/azure/search/retrieval-augmented-generation-overview)
- [Lesson format](../../../00-start-here/LEARNING-METHOD.md)
- [Deep-dive lesson template](../../../00-start-here/TEMPLATES.md)

## Completion gate
Mark **learned** only after explaining it unassisted, solving two unseen changed-constraint scenarios, and producing verification evidence. Reading and AI-generated summaries alone do not count.
