# Enterprise AI reference architecture (illustrative)

```mermaid
flowchart TB
  U[Users and business workflows] --> G[SSO / API gateway / authorization]
  G --> O[AI application / deterministic workflow]
  O --> R[Permission-aware retrieval]
  O --> M[Model gateway / routing]
  O --> T[Governed tool execution]
  S[Source systems: docs, SQL, streams] --> I[Ingestion, data contracts, ACL sync]
  I --> R
  T --> S
  O --> E[Evaluation and release gates]
  O --> H[Human review / audit]
  subgraph Cross_cutting[Cross-cutting controls]
    C[Policy, threat model, tracing, cost, operations]
  end
```

This is a **logical** diagram, not a claim of one universal reference solution. For classification, fraud scoring or edge AI the retrieval layer may be omitted; for high-risk actions use a separate policy and transaction execution service with bounded privileges.

## Design review checklist
- Business baseline, critical risks and outcome owner identified?
- Trusted identity, authorization, privacy and data location established?
- Model and retrieval access constrained? No untrusted data promoted to instructions?
- Durable state, recovery and unknown external outcomes modeled?
- Evaluation oracle and severity-weighted error criteria agreed?
- Monitoring, rollbacks, fallback modes and incident commander identified?
- Human approvals, auditability and policy exception process explicit?
