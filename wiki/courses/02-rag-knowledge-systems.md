# Course 02: RAG And Knowledge Systems

**Prerequisite:** [01](01-llm-application-engineering.md) · **Gate:** grounded-answer evaluation

Retrieval-augmented generation as a discipline, not a library call: ingest → parse → chunk → enrich → index → retrieve → rerank → assemble → generate-with-citations → evaluate, with authorization (document-level ACLs) enforced before ranking, not after. The failure-analysis list (poisoned documents, cross-tenant leakage, stale indexes, "citation-shaped" unsupported claims) reads like a checklist for exactly the kind of RAG layer [claims-workflow-v2-poc](../../../xingai-enterprise-ai-pocs/pocs/claims-workflow-v2-poc/) built in its Phase 2 (`mcp_server/rag.py`) — that POC's choice to skip a vector database for a small per-policy corpus is this course's "prefer long context for small stable corpora" guidance, applied.

## Connects to

- [Concept: Cache-first LLM architecture](../concepts/cache-first-llm-architecture.md) — RAG's retrieval step is itself a cache-vs-recompute decision at a different layer.
- The `recall_at_k` metric taught here is the same evaluation instinct Course 06 (Production AI Engineering) generalizes into golden/adversarial sets and release gates.

## Verified

`recall_at_k({"a","c"}, ["a","b","c"], 2) == 0.5` and `recall_at_k(..., 3) == 1.0` both checked by hand, correct. [RAG paper](https://arxiv.org/abs/2005.11401) (Lewis et al.) is the real, correct primary source for the technique. ZH sibling ingested 2026-07-16: Python code byte-identical, heading count matches (7/7).

## Sources

`raw/courses/02-rag-knowledge-systems.md`
