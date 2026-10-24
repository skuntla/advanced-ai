# S13 — Real-time and edge AI

## Why enterprises build this
Factory vision, low-latency sensor analytics and on-device intelligence.

## Reference architecture to draw
**Flow:** Device/sensor → preprocessing → local inference → event gate → cloud sync and monitoring.

Write out the system's inputs and source of truth, interfaces, model versus deterministic responsibilities, security principals, state and failure boundaries. Add one sync and one async sequence diagram and explicitly label irreversible effects.

## Architectural design decisions
Edge versus centralized inference; intermittent connectivity; privacy and power budget.

For each choice: define the nonfunctional requirements and measurable criteria that favor either option; record an ADR and the conditions that would reverse your decision.

## Concrete exercise
Design a minimal viable version with synthetic data. Have an AI coding agent challenge missing assumptions and sketch the APIs and state transitions. Before implementation, require a list of authorized roles, harmful outputs, adverse business effects and release criteria. Explain how you would validate the resulting system without relying on the same model as its only judge.

## Inject these failures
1. **Sensor drift** — describe trigger, observable trace, containment, remediation and regression test.
2. **stale firmware** — describe trigger, observable trace, containment, remediation and regression test.
3. **disconnected device** — describe trigger, observable trace, containment, remediation and regression test.
4. **unsafe actuation.** — describe trigger, observable trace, containment, remediation and regression test.

## Acceptance evidence
P99 inference latency, safety false negatives, availability, OTA reliability.

Demonstrate outcome quality, not only successful tool calls or a polished demo. Include representative distribution, worst-case severity, human escalation and operational readiness.

## Mastery interview
1. Walk from ambiguous executive request to validated business baseline and architecture.
2. What can be implemented without a generative model, and why?
3. Which trust boundary must the model never control?
4. What event can leave an external action in an unknown state?
5. Which metric would convince you **not** to launch?
6. Explain architecture and economics to a skeptical CTO in two minutes.

## Related topics
- Knowledge domains: D08,D11,D21,D22,D23
- Failure classes: F02,F04,F12
- [Study protocol](../../00-start-here/LEARNING-METHOD.md)
- [Reference architecture](../../00-start-here/REFERENCE-ARCHITECTURE.md)
