# S04 — Customer-facing conversational AI

## Why enterprises build this
Customer support chatbot, omnichannel account assistant and voice contact center.

## Reference architecture to draw
**Flow:** Identity verification → conversation state → intent/knowledge/tools → safe answer/action → escalation → analytics.

Write out the system's inputs and source of truth, interfaces, model versus deterministic responsibilities, security principals, state and failure boundaries. Add one sync and one async sequence diagram and explicitly label irreversible effects.

## Architectural design decisions
Human transfer thresholds; realtime latency versus depth; personalization versus privacy.

For each choice: define the nonfunctional requirements and measurable criteria that favor either option; record an ADR and the conditions that would reverse your decision.

## Concrete exercise
Design a minimal viable version with synthetic data. Have an AI coding agent challenge missing assumptions and sketch the APIs and state transitions. Before implementation, require a list of authorized roles, harmful outputs, adverse business effects and release criteria. Explain how you would validate the resulting system without relying on the same model as its only judge.

## Inject these failures
1. **Wrong account revealed** — describe trigger, observable trace, containment, remediation and regression test.
2. **speech misheard** — describe trigger, observable trace, containment, remediation and regression test.
3. **unsupported promise** — describe trigger, observable trace, containment, remediation and regression test.
4. **loop on handoff.** — describe trigger, observable trace, containment, remediation and regression test.

## Acceptance evidence
Containment rate with quality, verified resolution, harmful-error rate, p95 turn latency.

Demonstrate outcome quality, not only successful tool calls or a polished demo. Include representative distribution, worst-case severity, human escalation and operational readiness.

## Mastery interview
1. Walk from ambiguous executive request to validated business baseline and architecture.
2. What can be implemented without a generative model, and why?
3. Which trust boundary must the model never control?
4. What event can leave an external action in an unknown state?
5. Which metric would convince you **not** to launch?
6. Explain architecture and economics to a skeptical CTO in two minutes.

## Related topics
- Knowledge domains: D11,D12,D13,D16,D22
- Failure classes: F04,F05,F09,F11
- [Study protocol](../../00-start-here/LEARNING-METHOD.md)
- [Reference architecture](../../00-start-here/REFERENCE-ARCHITECTURE.md)
