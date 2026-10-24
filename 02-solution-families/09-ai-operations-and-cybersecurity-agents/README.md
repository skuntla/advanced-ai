# S09 — AI operations and cybersecurity agents

## Why enterprises build this
Log investigation, alert correlation, incident triage and guarded remediation.

## Reference architecture to draw
**Flow:** Telemetry → normalize and correlate → agent investigation → evidence-based diagnosis → policy approval → runbook execution.

Write out the system's inputs and source of truth, interfaces, model versus deterministic responsibilities, security principals, state and failure boundaries. Add one sync and one async sequence diagram and explicitly label irreversible effects.

## Architectural design decisions
Read-only triage versus write-capable remediation; host containment criteria.

For each choice: define the nonfunctional requirements and measurable criteria that favor either option; record an ADR and the conditions that would reverse your decision.

## Concrete exercise
Design a minimal viable version with synthetic data. Have an AI coding agent challenge missing assumptions and sketch the APIs and state transitions. Before implementation, require a list of authorized roles, harmful outputs, adverse business effects and release criteria. Explain how you would validate the resulting system without relying on the same model as its only judge.

## Inject these failures
1. **Alert fatigue** — describe trigger, observable trace, containment, remediation and regression test.
2. **incorrect containment** — describe trigger, observable trace, containment, remediation and regression test.
3. **poisoned log instruction** — describe trigger, observable trace, containment, remediation and regression test.
4. **loss of evidence.** — describe trigger, observable trace, containment, remediation and regression test.

## Acceptance evidence
MTTD, MTTR, incorrect action count, analyst review burden.

Demonstrate outcome quality, not only successful tool calls or a polished demo. Include representative distribution, worst-case severity, human escalation and operational readiness.

## Mastery interview
1. Walk from ambiguous executive request to validated business baseline and architecture.
2. What can be implemented without a generative model, and why?
3. Which trust boundary must the model never control?
4. What event can leave an external action in an unknown state?
5. Which metric would convince you **not** to launch?
6. Explain architecture and economics to a skeptical CTO in two minutes.

## Related topics
- Knowledge domains: D12,D13,D16,D17,D25
- Failure classes: F05,F06,F09,F13
- [Study protocol](../../00-start-here/LEARNING-METHOD.md)
- [Reference architecture](../../00-start-here/REFERENCE-ARCHITECTURE.md)
