# S14 — Optimization and planning systems

## Why enterprises build this
Workforce allocation, supply-chain optimization, scheduling and constraints.

## Reference architecture to draw
**Flow:** Define objective/constraints → ingest verified state → optimizer/solver → feasibility checks → authorized action.

Write out the system's inputs and source of truth, interfaces, model versus deterministic responsibilities, security principals, state and failure boundaries. Add one sync and one async sequence diagram and explicitly label irreversible effects.

## Architectural design decisions
Mathematical optimization versus LLM proposals; approximate heuristics vs exact solver.

For each choice: define the nonfunctional requirements and measurable criteria that favor either option; record an ADR and the conditions that would reverse your decision.

## Concrete exercise
Design a minimal viable version with synthetic data. Have an AI coding agent challenge missing assumptions and sketch the APIs and state transitions. Before implementation, require a list of authorized roles, harmful outputs, adverse business effects and release criteria. Explain how you would validate the resulting system without relying on the same model as its only judge.

## Inject these failures
1. **Infeasible schedule** — describe trigger, observable trace, containment, remediation and regression test.
2. **objective misalignment** — describe trigger, observable trace, containment, remediation and regression test.
3. **stale capacity** — describe trigger, observable trace, containment, remediation and regression test.
4. **unintended bias.** — describe trigger, observable trace, containment, remediation and regression test.

## Acceptance evidence
Constraint violations, objective value, operational improvement, recovery speed.

Demonstrate outcome quality, not only successful tool calls or a polished demo. Include representative distribution, worst-case severity, human escalation and operational readiness.

## Mastery interview
1. Walk from ambiguous executive request to validated business baseline and architecture.
2. What can be implemented without a generative model, and why?
3. Which trust boundary must the model never control?
4. What event can leave an external action in an unknown state?
5. Which metric would convince you **not** to launch?
6. Explain architecture and economics to a skeptical CTO in two minutes.

## Related topics
- Knowledge domains: D01,D02,D08,D15,D24
- Failure classes: F01,F02,F10
- [Study protocol](../../00-start-here/LEARNING-METHOD.md)
- [Reference architecture](../../00-start-here/REFERENCE-ARCHITECTURE.md)
