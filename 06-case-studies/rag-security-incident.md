# Case study — Unauthorized policy disclosure before launch

## Executive situation
A 200-person RAG pilot leaks a restricted compliance document to an Operations employee; 20% of pilot answers are reportedly wrong, p95/p99 latency is poor, and a company-wide launch is scheduled next week.

## The decision
Contain the exposure, activate incident response, preserve relevant evidence and restrict affected retrieval routes. Recommend **no company-wide launch** while serious exposure and quality defects are unresolved.

## Investigation
Trace trusted user claims → effective document ACL → index ACL snapshot → search filter → reranker → LLM context → response and cache. A correctly authenticated employee can still receive unauthorized material from a broken retrieval filter or shared cache.

Independently triage answer errors across parsing, freshness, search, reranking, generation and faulty feedback labeling. Instrument latency by identity, database, retrieval, reranking, model prefill/generation and agent tools before optimizing.

## Recovery and accountability
Reproduce exact exploit with synthetic comparable test identity, remediate at service boundary, backfill tests for revocations, alternate endpoints, caches and multi-tenant isolation. Have security assess exposure; require explicit quality, security, reliability and operations acceptance criteria before resuming.
