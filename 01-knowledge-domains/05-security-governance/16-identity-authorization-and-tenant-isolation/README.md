# Domain 16 — Identity, authorization and tenant isolation

> Pillar 5: Security, Privacy and Governance · Status: **curriculum chapter / guided study** · Depth target: explain → design → challenge → prove.

## Why this matters
Enforce boundaries independently of a model and demonstrate risk accountability. In this domain, the architect needs more than terminology: they must choose an approach, specify its guarantees, and defend its limits.

## Learning outcomes
After studying this domain you should be able to:
1. Explain every essential mechanism below in plain English and at implementation depth.
2. Draw a production-grade design with trust boundaries, dependencies and failure states.
3. Identify non-obvious assumptions; compare alternatives based on business risk.
4. Use AI coding agents to prototype experiments, then independently verify outcomes.
5. Answer the scenario questions cold, without relying on AI-generated answers.

## Detailed concept checklist
1. **Authentication vs authorization** — define it; explain the internals; when to use it; where it fails; how to verify it.
2. **RBAC** — define it; explain the internals; when to use it; where it fails; how to verify it.
3. **ABAC** — define it; explain the internals; when to use it; where it fails; how to verify it.
4. **ACL** — define it; explain the internals; when to use it; where it fails; how to verify it.
5. **SSO** — define it; explain the internals; when to use it; where it fails; how to verify it.
6. **JWT validation** — define it; explain the internals; when to use it; where it fails; how to verify it.
7. **delegated access** — define it; explain the internals; when to use it; where it fails; how to verify it.
8. **row-level security** — define it; explain the internals; when to use it; where it fails; how to verify it.
9. **tenant isolation** — define it; explain the internals; when to use it; where it fails; how to verify it.
10. **caching** — define it; explain the internals; when to use it; where it fails; how to verify it.

## Walkthrough scenario
**Problem:** Operations employee may query one shared vector index but must never receive confidential compliance chunks.

**How to reason about it:**
1. Identify the authoritative business facts, risk boundaries, actors and measurable success.
2. Separate **facts**, **assumptions**, **model inferences**, and **decisions**; obtain independent evidence.
3. Draw the minimal flow from input through state, data/tools, decision and output/action.
4. Define both happy path and failure path, including visibility, retry/recovery and human escalation.
5. Define tests and release criteria before authorizing AI-assisted implementation.

**Architectural trade-off:** Enforce access at trusted service/data boundary; verify revocations and inherited permissions.

## Failure laboratory
Investigate each of these as a reproducible failure hypothesis:
1. Cross-tenant cache hit. Record the trigger, blast radius, evidence, containment, durable fix and regression test.
2. stale entitlements. Record the trigger, blast radius, evidence, containment, durable fix and regression test.
3. endpoint bypass. Record the trigger, blast radius, evidence, containment, durable fix and regression test.
4. policy mismatch.. Record the trigger, blast radius, evidence, containment, durable fix and regression test.

## Decision and review questions
- How can a shared vector DB be secure?
- How do you enforce deny-by-default?
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
- [Primary reference](https://learn.microsoft.com/en-us/azure/search/search-document-level-access-overview)
- [Pillar reference](https://www.nist.gov/itl/ai-risk-management-framework)
- [Lesson format](../../../../00-start-here/LEARNING-METHOD.md)
- [Deep-dive lesson template](../../../../00-start-here/TEMPLATES.md)

## Completion gate
Mark **learned** only after explaining it unassisted, solving two unseen changed-constraint scenarios, and producing verification evidence. Reading and AI-generated summaries alone do not count.
