# F06 — Adversarial failure

## Failure definition
Prompt injection, malicious tool responses and poisoned content.

## Illustrative incident
Retrieved PDF instructs agent to export internal financial records.

This is a synthetic practice scenario; it is not a reported real-world incident.

## First response / containment
Block tool execution, isolate inputs, rotate compromised credentials and investigate.

Explicitly identify accountable incident leader, user impact, affected data/actions, change freeze, preservation of evidence and notification/escalation per company procedure. Distinguish **containment** from root-cause fix.

## Diagnose with evidence
Input/provenance chain, tool decision trace, egress logs, sandbox evidence.

Create a timeline and at least three competing hypotheses. Identify which observations falsify each hypothesis. Do not infer an operation failed solely because its HTTP response timed out or its model response said 'failed'.

## Design to prevent recurrence
Untrusted content separation, allowlisted actions/egress, red-team regression.

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
D13,D17,D18 · [Master failure index](../README.md) · [Runbook template](../../00-start-here/TEMPLATES.md).
