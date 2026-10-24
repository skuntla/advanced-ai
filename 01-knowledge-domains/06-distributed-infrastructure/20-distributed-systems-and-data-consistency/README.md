# Domain 20 — Distributed systems and data consistency

> Pillar 6: Distributed Systems and AI Infrastructure · Status: **curriculum chapter / guided study** · Depth target: explain → design → challenge → prove.

## Guided learning: start here

- [Domain 20 ten-module roadmap](MODULE-ROADMAP.md) — ordered syllabus, questions and exit evidence.
- [Module 01: Distributed-system fundamentals](module-01-fundamentals/README.md) — first interactive micro-lesson.
- [Chat-first learning workflow](../../../00-start-here/CHAT-FIRST-WORKFLOW.md) — how we turn discussion into verified standalone documentation.

**Status:** Domain outline established; Module 01 started on 2026-10-24. No learning/mastery claim is made until independently demonstrated.

## Why this matters
Preserve correctness through partial failure while controlling latency, reliability and cost. In this domain, the architect needs more than terminology: they must choose an approach, specify its guarantees, and defend its limits.

## Learning outcomes
After studying this domain you should be able to:
1. Explain every essential mechanism below in plain English and at implementation depth.
2. Draw a production-grade design with trust boundaries, dependencies and failure states.
3. Identify non-obvious assumptions; compare alternatives based on business risk.
4. Use AI coding agents to prototype experiments, then independently verify outcomes.
5. Answer the scenario questions cold, without relying on AI-generated answers.

## Detailed concept checklist
1. **Timeouts** — define it; explain the internals; when to use it; where it fails; how to verify it.
2. **retries** — define it; explain the internals; when to use it; where it fails; how to verify it.
3. **idempotency** — define it; explain the internals; when to use it; where it fails; how to verify it.
4. **deduplication** — define it; explain the internals; when to use it; where it fails; how to verify it.
5. **Kafka semantics** — define it; explain the internals; when to use it; where it fails; how to verify it.
6. **transactions** — define it; explain the internals; when to use it; where it fails; how to verify it.
7. **saga** — define it; explain the internals; when to use it; where it fails; how to verify it.
8. **outbox** — define it; explain the internals; when to use it; where it fails; how to verify it.
9. **compensating actions** — define it; explain the internals; when to use it; where it fails; how to verify it.
10. **leases** — define it; explain the internals; when to use it; where it fails; how to verify it.
11. **concurrency** — define it; explain the internals; when to use it; where it fails; how to verify it.

## Walkthrough scenario
**Problem:** System A commits while B times out without idempotency or status API; record unknown outcome and reconcile, not blindly retry.

**How to reason about it:**
1. Identify the authoritative business facts, risk boundaries, actors and measurable success.
2. Separate **facts**, **assumptions**, **model inferences**, and **decisions**; obtain independent evidence.
3. Draw the minimal flow from input through state, data/tools, decision and output/action.
4. Define both happy path and failure path, including visibility, retry/recovery and human escalation.
5. Define tests and release criteria before authorizing AI-assisted implementation.

**Architectural trade-off:** Specify guarantees at business-effect level, not merely messaging level.

## Failure laboratory
Investigate each of these as a reproducible failure hypothesis:
1. Duplicate correction. Record the trigger, blast radius, evidence, containment, durable fix and regression test.
2. silent partial commit. Record the trigger, blast radius, evidence, containment, durable fix and regression test.
3. replay collision. Record the trigger, blast radius, evidence, containment, durable fix and regression test.
4. inconsistent ledger.. Record the trigger, blast radius, evidence, containment, durable fix and regression test.

## Decision and review questions
- Can you prove exactly-once external effects?
- When must automation stop?
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
- [Primary reference](https://aws.amazon.com/builders-library/making-retries-safe-with-idempotent-APIs/)
- [Pillar reference](https://aws.amazon.com/builders-library/)
- [Lesson format](../../../00-start-here/LEARNING-METHOD.md)
- [Deep-dive lesson template](../../../00-start-here/TEMPLATES.md)

## Completion gate
Mark **learned** only after explaining it unassisted, solving two unseen changed-constraint scenarios, and producing verification evidence. Reading and AI-generated summaries alone do not count.
