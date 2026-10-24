# Domain 20 — Ten-module guided learning roadmap

**Domain:** Distributed systems and data consistency · **Approach:** [chat-first mastery](../../../00-start-here/CHAT-FIRST-WORKFLOW.md) · **Status:** Roadmap established; Module 01 in progress; no mastery asserted.

## What this domain must enable

The learner should be able to design and defend business-correct workflows across independently failing components; distinguish a response timeout from a failed side effect; reason about coordination, concurrency, ordering and consistency; implement or simulate failure cases; and know when to stop automation and reconcile externally.

Each module uses: *driving puzzle → simple intuition → internal mechanics → small trace/numbers → diagram → alternatives → enterprise example → failure injections → evidence → one-at-a-time adaptive interview → check-in*.

| Module | Topic | Micro-topics and expected reasoning | Completion evidence |
|---|---|---|---|
| **01** | [Distributed-system fundamentals](module-01-fundamentals/README.md) | Processes vs network; why distribute; synchronous/asynchronous communication; independent and partial failures; missing/late messages; clocks, ordering and observations; key invariants | Explain why another service's state cannot be inferred from a missing response; draw a two-service trace |
| **02** | Communication and failure semantics | Request/response; ACKs; timeouts; deadline propagation; lost responses; unknown outcomes; health signals; failure detectors | Analyze all possible remote states after a timeout |
| **03** | Retries, backoff and idempotency | Retryable vs unsafe operations; request IDs; dedup stores; request payload mismatches; jitter; poison retries; no-idempotency APIs | Design a safe replay contract, including cases where safe retry is impossible |
| **04** | Messaging and delivery guarantees | Kafka topics/partitions, consumer groups, ordering, offset commits, duplicate delivery, rebalances, at-least/at-most-once and scoped exactly-once guarantees | Draw failure/replay timelines and state the guarantee at business-effect boundary |
| **05** | Transactions and consistency | ACID; isolation levels, lost updates, write skew; consistency models; replication; read-your-writes; transactional boundaries | Identify which business invariants are preserved by a chosen isolation/consistency model |
| **06** | Event-driven data integrity | Outbox, inbox, CDC, event versioning, schema evolution, replay, event sourcing, reconciliation | Show how to publish an event without creating a silent dual-write gap |
| **07** | Distributed workflow patterns | Saga orchestration/choreography; compensation vs rollback; step state; temporal ordering; durable workflow engines | Model a multi-step transaction with failure-specific paths |
| **08** | Concurrency and coordination | Race conditions, optimistic/pessimistic locking, leases, fencing tokens, leader selection, clock caveats | Diagnose double processing despite a lease or lock |
| **09** | Recovery and reconciliation | Durable recovery state, conflicting records, manual verification, external authority, audit trail, irreversible effects | Safely handle an API that has neither idempotency nor a trustworthy status endpoint |
| **10** | Production architecture mastery | End-to-end invariants, reliability budgets, failover, tracing, load/backpressure, chaos tests, costs, ADRs, disaster scenarios | Unassisted architecture defense and test plan for a regulated financial workflow |

## Module 01 exact micro-learning sequence

1. **1.1 — What makes a system distributed?** Boundaries: a process, another process, a network.
2. **1.2 — Why distribute?** Independent scaling, separation and fault domains; complexity incurred.
3. **1.3 — Communication models.** Requests, queues, events; latency and message delivery.
4. **1.4 — Partial failure.** Service healthy while connection is not; late and duplicate responses; state versus observation.
5. **1.5 — Clocks and ordering.** Wall clock vs monotonic time, skew and happens-before as intuition.
6. **1.6 — Invariants and design promises.** Business correctness, availability and error budgets; define observable guarantees.

**Module 01 exit gate:** Describe the minimum architecture, distinguish at least four plausible causes of silence, explain what evidence each would require, and defend a simple correctness invariant. No broad claim of mastering distributed systems after one question.

## Learning artifacts as modules complete

- `module-NN-.../README.md`: goals, syllabus, verified explanation and references.
- `module-NN-.../lessons/<microtopic>.md`: publish after interactive discussion and verification (not before).
- Optional diagram / trace files, synthetic experiments, ADRs, tests and incident runbooks as warranted.
- Update [PROGRESS](../../../00-start-here/PROGRESS.md) with actual outcome, date, evidence and next review.
- Finish with a domain-level unknown-outcome trade/settlement architecture exercise and changed-constraint defense.

The ten folders do not need to be created in advance: create each when it has actual content.

## Recommended references (supplement explanations)

- [AWS Builders' Library — Timeouts, retries, and backoff with jitter](https://aws.amazon.com/builders-library/timeouts-retries-and-backoff-with-jitter/)
- [AWS Builders' Library — Making retries safe with idempotent APIs](https://aws.amazon.com/builders-library/making-retries-safe-with-idempotent-APIs/)
- [Designing Data-Intensive Applications — book site](https://dataintensive.net/)
- [Google SRE Books](https://sre.google/books/)
- [Domain 20 chapter](README.md)
- [Existing worked example — unknown outcome and idempotency](../../../04-worked-lessons/unknown-outcome-and-idempotency.md)

**Source note:** Reading references is part of research; they do not substitute for independent verification of your particular architectural claims.
