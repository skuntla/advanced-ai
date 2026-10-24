# F11 — Performance failure

## Failure definition
Latency, resource exhaustion and throughput shortfall.

## Illustrative incident
RAG p99 spikes to 25 seconds under peak load.

This is a synthetic practice scenario; it is not a reported real-world incident.

## First response / containment
Protect SLO with admission control, bypass nonessential steps, diagnose bottleneck.

Explicitly identify accountable incident leader, user impact, affected data/actions, change freeze, preservation of evidence and notification/escalation per company procedure. Distinguish **containment** from root-cause fix.

## Diagnose with evidence
Per-stage distributed traces, token counts, queue depth, DB latency.

Create a timeline and at least three competing hypotheses. Identify which observations falsify each hypothesis. Do not infer an operation failed solely because its HTTP response timed out or its model response said 'failed'.

## Design to prevent recurrence
Load testing, budgets, efficient retrieval, batching, caching with isolation.

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
D06,D22,D23,D25 · [Master failure index](../README.md) · [Runbook template](../../00-start-here/TEMPLATES.md).
