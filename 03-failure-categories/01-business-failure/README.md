# F01 — Business failure

## Failure definition
Solution does not solve the right problem or create measurable value.

## Illustrative incident
Benefit hypothesis lacks real baseline; users abandon a technically correct pilot.

This is a synthetic practice scenario; it is not a reported real-world incident.

## First response / containment
Pause expansion, observe real workflows, compare manual counterfactual and fix product scope.

Explicitly identify accountable incident leader, user impact, affected data/actions, change freeze, preservation of evidence and notification/escalation per company procedure. Distinguish **containment** from root-cause fix.

## Diagnose with evidence
Product analytics, user interviews, measured before/after handling time.

Create a timeline and at least three competing hypotheses. Identify which observations falsify each hypothesis. Do not infer an operation failed solely because its HTTP response timed out or its model response said 'failed'.

## Design to prevent recurrence
Baseline and control group, clear outcome owner, go/no-go criteria.

Turn the failure into regression/chaos/security evaluations; test blast radius, state consistency, access boundaries, rollbacks and recovered business invariants.

## Practical laboratory
- Generate synthetic inputs representing the normal workflow.
- Inject the failure deliberately: write down expected symptoms **before** executing.
- Ask AI to create a reproducer and diagnostic instrumentation, not immediately to 'fix it'.
- Compare logs/state to independent oracle; trace unauthorized side effects.
- Implement a small remediation; replay and verify negative and positive cases.

## Interview defense
1. What is the first action, and why?
2. How would you distinguish five plausible causes?
3. What cannot be concluded from the evidence you currently have?
4. When do you choose human intervention, fallback or shutdown?
5. What is the release gate and who can accept residual risk?
6. Explain the incident briefly to the CTO without hiding uncertainty.

## Related domains
D01,D02,D03,D27 · [Master failure index](../README.md) · [Runbook template](../../00-start-here/TEMPLATES.md).
