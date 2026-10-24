# S08 — Software engineering agents

## Why enterprises build this
Code generation, refactoring, migrations and test-automation systems.

## Reference architecture to draw
**Flow:** Task specification → repo context → isolated execution → code changes/tests → independent review → gated merge.

Write out the system's inputs and source of truth, interfaces, model versus deterministic responsibilities, security principals, state and failure boundaries. Add one sync and one async sequence diagram and explicitly label irreversible effects.

## Architectural design decisions
Autonomous code changes versus human approval; repository access scope; sandbox costs.

For each choice: define the nonfunctional requirements and measurable criteria that favor either option; record an ADR and the conditions that would reverse your decision.

## Concrete exercise
Design a minimal viable version with synthetic data. Have an AI coding agent challenge missing assumptions and sketch the APIs and state transitions. Before implementation, require a list of authorized roles, harmful outputs, adverse business effects and release criteria. Explain how you would validate the resulting system without relying on the same model as its only judge.

## Inject these failures
1. **Unsafe dependency** — describe trigger, observable trace, containment, remediation and regression test.
2. **prompt injection from repo** — describe trigger, observable trace, containment, remediation and regression test.
3. **bogus passing tests** — describe trigger, observable trace, containment, remediation and regression test.
4. **secret leak.** — describe trigger, observable trace, containment, remediation and regression test.

## Acceptance evidence
Build pass, independent regression, exploit scan, change failure rate.

Demonstrate outcome quality, not only successful tool calls or a polished demo. Include representative distribution, worst-case severity, human escalation and operational readiness.

## Mastery interview
1. Walk from ambiguous executive request to validated business baseline and architecture.
2. What can be implemented without a generative model, and why?
3. Which trust boundary must the model never control?
4. What event can leave an external action in an unknown state?
5. Which metric would convince you **not** to launch?
6. Explain architecture and economics to a skeptical CTO in two minutes.

## Related topics
- Knowledge domains: D12,D13,D17,D24,D27
- Failure classes: F05,F06,F09,F13
- [Study protocol](../../00-start-here/LEARNING-METHOD.md)
- [Reference architecture](../../00-start-here/REFERENCE-ARCHITECTURE.md)
