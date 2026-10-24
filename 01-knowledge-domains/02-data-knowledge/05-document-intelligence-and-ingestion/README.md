# Domain 05 — Document intelligence and ingestion

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
1. **PDF and OCR extraction** — define it; explain the internals; when to use it; where it fails; how to verify it.
2. **section parsing** — define it; explain the internals; when to use it; where it fails; how to verify it.
3. **tables** — define it; explain the internals; when to use it; where it fails; how to verify it.
4. **layouts** — define it; explain the internals; when to use it; where it fails; how to verify it.
5. **chunk boundaries** — define it; explain the internals; when to use it; where it fails; how to verify it.
6. **deduplication** — define it; explain the internals; when to use it; where it fails; how to verify it.
7. **content hashes** — define it; explain the internals; when to use it; where it fails; how to verify it.
8. **incremental updates** — define it; explain the internals; when to use it; where it fails; how to verify it.
9. **deletion** — define it; explain the internals; when to use it; where it fails; how to verify it.
10. **effective dating** — define it; explain the internals; when to use it; where it fails; how to verify it.

## Walkthrough scenario
**Problem:** A 90-page compliance manual changes one section: update affected chunks, version metadata and authorization promptly.

**How to reason about it:**
1. Identify the authoritative business facts, risk boundaries, actors and measurable success.
2. Separate **facts**, **assumptions**, **model inferences**, and **decisions**; obtain independent evidence.
3. Draw the minimal flow from input through state, data/tools, decision and output/action.
4. Define both happy path and failure path, including visibility, retry/recovery and human escalation.
5. Define tests and release criteria before authorizing AI-assisted implementation.

**Architectural trade-off:** Compare document-level versus section-level chunking; preserve table and footnote meaning.

## Failure laboratory
Investigate each of these as a reproducible failure hypothesis:
1. OCR corrupts numbers. Record the trigger, blast radius, evidence, containment, durable fix and regression test.
2. a deleted chunk survives. Record the trigger, blast radius, evidence, containment, durable fix and regression test.
3. ACL change lags behind search index.. Record the trigger, blast radius, evidence, containment, durable fix and regression test.

## Decision and review questions
- What must change when an ACL is revoked?
- How do you prevent mixing outdated and current policy?
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
- [Primary reference](https://learn.microsoft.com/en-us/azure/search/search-how-to-indexing-azure-blob-storage)
- [Pillar reference](https://learn.microsoft.com/en-us/azure/search/retrieval-augmented-generation-overview)
- [Lesson format](../../../../00-start-here/LEARNING-METHOD.md)
- [Deep-dive lesson template](../../../../00-start-here/TEMPLATES.md)

## Completion gate
Mark **learned** only after explaining it unassisted, solving two unseen changed-constraint scenarios, and producing verification evidence. Reading and AI-generated summaries alone do not count.
