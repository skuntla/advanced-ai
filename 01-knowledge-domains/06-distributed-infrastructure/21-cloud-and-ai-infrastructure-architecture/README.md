# Domain 21 — Cloud and AI infrastructure architecture

> Pillar 6: Distributed Systems and AI Infrastructure · Status: **curriculum chapter / guided study** · Depth target: explain → design → challenge → prove.

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
1. **AWS/Azure/GCP** — define it; explain the internals; when to use it; where it fails; how to verify it.
2. **network segmentation** — define it; explain the internals; when to use it; where it fails; how to verify it.
3. **IAM** — define it; explain the internals; when to use it; where it fails; how to verify it.
4. **containers** — define it; explain the internals; when to use it; where it fails; how to verify it.
5. **Kubernetes** — define it; explain the internals; when to use it; where it fails; how to verify it.
6. **serverless** — define it; explain the internals; when to use it; where it fails; how to verify it.
7. **IaC** — define it; explain the internals; when to use it; where it fails; how to verify it.
8. **deployment regions** — define it; explain the internals; when to use it; where it fails; how to verify it.
9. **storage** — define it; explain the internals; when to use it; where it fails; how to verify it.
10. **high availability** — define it; explain the internals; when to use it; where it fails; how to verify it.

## Walkthrough scenario
**Problem:** Deploy a customer-facing AI service privately connected to internal datasets with regional recovery.

**How to reason about it:**
1. Identify the authoritative business facts, risk boundaries, actors and measurable success.
2. Separate **facts**, **assumptions**, **model inferences**, and **decisions**; obtain independent evidence.
3. Draw the minimal flow from input through state, data/tools, decision and output/action.
4. Define both happy path and failure path, including visibility, retry/recovery and human escalation.
5. Define tests and release criteria before authorizing AI-assisted implementation.

**Architectural trade-off:** Choose managed services versus self-hosting according to security, load and operating burden.

## Failure laboratory
Investigate each of these as a reproducible failure hypothesis:
1. Provider outage. Record the trigger, blast radius, evidence, containment, durable fix and regression test.
2. network misconfiguration. Record the trigger, blast radius, evidence, containment, durable fix and regression test.
3. secrets leak. Record the trigger, blast radius, evidence, containment, durable fix and regression test.
4. regional failover failure.. Record the trigger, blast radius, evidence, containment, durable fix and regression test.

## Decision and review questions
- What SLO determines deployment architecture?
- What happens during regional outage?
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
- [Primary reference](https://aws.amazon.com/architecture/well-architected/)
- [Pillar reference](https://aws.amazon.com/builders-library/)
- [Lesson format](../../../../00-start-here/LEARNING-METHOD.md)
- [Deep-dive lesson template](../../../../00-start-here/TEMPLATES.md)

## Completion gate
Mark **learned** only after explaining it unassisted, solving two unseen changed-constraint scenarios, and producing verification evidence. Reading and AI-generated summaries alone do not count.
