# Permission-aware RAG — one index, many access policies

**Related domains:** D05, D06, D16, D17. **Design invariant:** restricted source text must not reach an unauthorized user or an LLM request created on their behalf.

## Intuition
A vector index needn't be a SQL table, but most vector systems store a record ID, embedding, text/pointer and structured payload/metadata. Search uses numerical similarity; metadata filters narrow eligible records. **The database does not automatically know the employee's authorization.** A trusted policy-enforcing service must control it.

## Tiny illustrative dataset
| Chunk | Policy text | Access |
| --- | --- | --- |
| C-1 | Holiday schedule | all_employees |
| C-2 | Settlement exception procedure | operations |
| C-3 | Confidential case investigation | compliance_case_17 |

Employee E100 belongs to `operations` and `all_employees`, **not** `compliance_case_17`. Unrestricted similarity search could rank C-3 highest. A search filtered by trusted entitlements must exclude C-3.

### Conceptual query
```python
# Pseudocode: actual syntax and security capabilities differ by vector provider.
identity = verify_session(session_token)
allowed_resource_ids = policy_service.authorized_documents(identity, now)
results = search_service.search(
    embedding=embed(user_question),
    filter={"document_id": {"in": allowed_resource_ids}},
    limit=8,
)
verified = [c for c in results if policy_service.can_read(identity, c.document_id)]
context = compose_model_context(verified)  # no unauthorized text included
```

Never accept allowed IDs/groups from user-provided prompt text. Do not expose unrestricted search credentials or an unrestricted retriever as a model-selected tool. A second authorization check is prudent for sources with fast-changing permissions.

## Can everything live in one physical database?
Often yes, when the vector/search technology can enforce metadata filtering or row/tenant-level isolation at a **trusted boundary**, with adequate side-channel and caching controls. Separate collections/databases can be justified by regulatory boundaries, encryption keys, residency, severe blast-radius concerns or workload isolation. Either design still needs correct identity and authorization.

## Failure scenarios
- Document reclassified at noon but index ACL updated at midnight.
- Retrieved chunk denied, but text already entered an agent's scratchpad before the final output filter.
- Cached answer produced for Compliance served to Operations.
- Reranker uses an unauthorized candidate before the authorized subset is applied.
- Identity token valid but group membership stale after revocation.
- Public and restricted sections of same document are chunked without distinct ACLs.

## Release verification
Replay authorized and denied users across every endpoint, caches, citation fetches, reranking stage, document revisions and tool call. Prove that denied content never reaches model context or visible output. Run denial and legitimate-access tests. Inspect source permissions, index metadata and effective token claims at the precise time of access.

## Sources
- [Azure AI Search document-level access](https://learn.microsoft.com/en-us/azure/search/search-document-level-access-overview)
- [OWASP GenAI security guidance](https://genai.owasp.org/llm-top-10/)
