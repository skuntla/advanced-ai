# S05 — Decision intelligence and analytics

## Why enterprises build this
Financial research, text-to-SQL, BI copilots and explainable decision support.

## Reference architecture to draw
**Flow:** Business question → semantic layer + authorized data tools → validated query → deterministic computations → narrative with provenance.

Write out the system's inputs and source of truth, interfaces, model versus deterministic responsibilities, security principals, state and failure boundaries. Add one sync and one async sequence diagram and explicitly label irreversible effects.

## Architectural design decisions
Freeform SQL versus governed metrics; materialization versus live queries.

For each choice: define the nonfunctional requirements and measurable criteria that favor either option; record an ADR and the conditions that would reverse your decision.

## Concrete exercise
Design a minimal viable version with synthetic data. Have an AI coding agent challenge missing assumptions and sketch the APIs and state transitions. Before implementation, require a list of authorized roles, harmful outputs, adverse business effects and release criteria. Explain how you would validate the resulting system without relying on the same model as its only judge.

## Inject these failures
1. **Hallucinated KPI** — describe trigger, observable trace, containment, remediation and regression test.
2. **wrong joins** — describe trigger, observable trace, containment, remediation and regression test.
3. **cross-tenant aggregation** — describe trigger, observable trace, containment, remediation and regression test.
4. **stale results.** — describe trigger, observable trace, containment, remediation and regression test.

## Acceptance evidence
Metric parity with finance controls, SQL validity, human decision usefulness.

Demonstrate outcome quality, not only successful tool calls or a polished demo. Include representative distribution, worst-case severity, human escalation and operational readiness.

## Mastery interview
1. Walk from ambiguous executive request to validated business baseline and architecture.
2. What can be implemented without a generative model, and why?
3. Which trust boundary must the model never control?
4. What event can leave an external action in an unknown state?
5. Which metric would convince you **not** to launch?
6. Explain architecture and economics to a skeptical CTO in two minutes.

## Related topics
- Knowledge domains: D01,D04,D08,D13,D24
- Failure classes: F01,F02,F04
- [Study protocol](../../00-start-here/LEARNING-METHOD.md)
- [Reference architecture](../../00-start-here/REFERENCE-ARCHITECTURE.md)
