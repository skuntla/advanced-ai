# Learning contract — understand, challenge, verify, own

## The lesson sequence (repeat for every subtopic)
1. **Ten-year-old intuition:** what problem is being solved? One memorable analogy; state where analogy breaks.
2. **First principles:** define the objects, invariants and mathematical/algorithmic mechanism. Use small numbers to calculate a complete example.
3. **System diagram:** show inputs, outputs, state, security boundary, authority, model and deterministic components.
4. **Alternatives:** compare at least three approaches with latency, correctness, cost, privacy, complexity and operational risk.
5. **Failure atlas:** explore false inputs, unknown outcomes, attack paths, partial failure, drift, stale data, concurrency and blast radius.
6. **Evidence:** specify an independent oracle, replayable test, logs/traces and acceptance criteria. Distinguish simulated results from production proof.
7. **AI-assisted laboratory:** provide rich context; instruct AI to identify assumptions and threats *before coding*. Challenge it. Let it implement a small falsifiable experiment.
8. **Cold interview:** explain, decide, defend and diagnose a fresh scenario with no assistant. Follow-ups change one constraint at a time.
9. **Spaced recall:** review after 1, 3, 7, 14 and 30 days; track missed concepts and revisit experimentally.

## One 90-minute session
- 30m explanation + worked numerical example
- 20m ask 'why', 'what if' and comparison questions
- 20m small AI-generated experiment / trace inspection
- 15m cold oral defense
- 5m spaced-repetition notes and next question

## Mastery rubric (0–4 independently scored)
- **0 Unseen:** terminology unfamiliar.
- **1 Recognize:** can recall terminology after hints.
- **2 Explain:** clear mechanism and example without notes.
- **3 Design:** select pattern, argue trade-offs, identify failure cases in new scenario.
- **4 Prove & own:** demonstrate falsifiable evidence, design controls, incident decision and business acceptance in unfamiliar scenario.

Do not claim Level 4 from watching videos or observing AI-generated output alone. Record a date, evidence path and reviewer notes.

## Context-first AI collaborator instructions
Before writing code, ask AI to: restate objectives and non-goals, inventory data/permissions, enumerate assumptions and unknowns, propose alternative designs, create a failure-mode table, specify invariant and release criteria, and identify test or evidence needed to falsify each claim. Question it until trade-offs are clear; authorize an experiment, not a blind production deployment.

## Explanation writing standard
Every explanation includes: **what / why / how / numbers / diagram / where it fails / how to verify / when not to use / authoritative resources**. Avoid misleading claims such as 'confidence=correctness', 'Kafka gives exactly-once side effects', or 'vector DB metadata alone guarantees access control'.
