# Reusable content templates

## Deep-dive domain lesson
Copy this outline into a new `lessons/<topic>.md` beside the relevant domain README.

1. **Driving question:** one precise misconception or puzzle.
2. **Plain-language explanation:** analogy and its limitations.
3. **Mechanics:** symbols, invariants, and 4×4 or otherwise small worked numerical example.
4. **Visual flow:** Mermaid sequence/component/state diagram with labeled trust boundaries.
5. **Alternative designs:** decision matrix including 'no AI needed'.
6. **Enterprise case:** data source, users, policy, throughput, business consequence.
7. **Failure injections:** expected observation, wrong approach, safe design, recovery.
8. **Verification:** oracle, unit/integration/invariant tests, traces, release thresholds.
9. **Sources:** official docs or papers; distinguish sourced facts from illustrative assumptions.
10. **Mastery test:** 3 recall, 3 trade-off, 2 diagnostics and 2 adversarial follow-ups.
11. **Spaced recall:** 1/3/7/14/30-day prompts.

## Solution design exercise
Problem → stakeholders → baseline → threat model → requirements → architectural alternatives → selected diagram → interfaces → authorization & state → quality metrics → rollout → owner & runbook → ADR → open risks.

## Failure runbook
**Symptom / scope / severity / containment / evidence preservation / timeline / competing hypotheses / root cause / blast radius / remediation / compensating actions / regression checks / residual risk / release decision / owner.**

## Architecture decision record
- Context and decision drivers
- Alternatives and measured evidence
- Chosen decision and rejected choices
- Trust boundaries and business invariants
- Consequences, reversibility, costs
- Review date and accountable owner
