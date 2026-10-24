# S06 — Predictive AI and anomaly detection

## Why enterprises build this
Fraud scoring, reconciliation anomaly detection, forecasting and risk models.

## Reference architecture to draw
**Flow:** Data contracts → feature pipeline → train/validate → low-latency scoring → thresholds → feedback and drift monitoring.

Write out the system's inputs and source of truth, interfaces, model versus deterministic responsibilities, security principals, state and failure boundaries. Add one sync and one async sequence diagram and explicitly label irreversible effects.

## Architectural design decisions
Gradient boosting versus neural model; false positive costs vs detection sensitivity; online vs batch.

For each choice: define the nonfunctional requirements and measurable criteria that favor either option; record an ADR and the conditions that would reverse your decision.

## Concrete exercise
Design a minimal viable version with synthetic data. Have an AI coding agent challenge missing assumptions and sketch the APIs and state transitions. Before implementation, require a list of authorized roles, harmful outputs, adverse business effects and release criteria. Explain how you would validate the resulting system without relying on the same model as its only judge.

## Inject these failures
1. **Label leakage** — describe trigger, observable trace, containment, remediation and regression test.
2. **drift** — describe trigger, observable trace, containment, remediation and regression test.
3. **adversarial transactions** — describe trigger, observable trace, containment, remediation and regression test.
4. **class imbalance.** — describe trigger, observable trace, containment, remediation and regression test.

## Acceptance evidence
PR-AUC, cost-weighted loss, recall at review capacity, calibration, drift.

Demonstrate outcome quality, not only successful tool calls or a polished demo. Include representative distribution, worst-case severity, human escalation and operational readiness.

## Mastery interview
1. Walk from ambiguous executive request to validated business baseline and architecture.
2. What can be implemented without a generative model, and why?
3. Which trust boundary must the model never control?
4. What event can leave an external action in an unknown state?
5. Which metric would convince you **not** to launch?
6. Explain architecture and economics to a skeptical CTO in two minutes.

## Related topics
- Knowledge domains: D04,D08,D19,D24,D26
- Failure classes: F02,F04,F14
- [Study protocol](../../00-start-here/LEARNING-METHOD.md)
- [Reference architecture](../../00-start-here/REFERENCE-ARCHITECTURE.md)
