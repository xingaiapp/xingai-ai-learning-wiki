# Course 01: LLM Application Engineering

**Prerequisite:** [00 AI Foundations](00-ai-foundations.md) · **Gate:** typed, tested application · **Next:** [02](02-rag-knowledge-systems.md), [03](03-tool-use-ai-agents.md)

The pivot from "understand models" to "build with them": an LLM application is conventional software around a probabilistic-model boundary. The load-bearing idea is placing model calls behind a service boundary and validating output with a typed schema (`parse_triage` in the raw source) instead of trusting free text — the same discipline [xingai-learn](../products/xingai-learn.md)'s engines apply for real, and the same discipline [claims-workflow-v2-poc](../../../xingai-enterprise-ai-pocs/pocs/claims-workflow-v2-poc/) applies with its heuristic/LLM dual-path fallback.

Two other courses branch from here rather than one: 02 (RAG) and 03 (Tool Use/Agents) both assume this course's typed-boundary discipline but extend it in different directions (retrieval vs. action).

## Connects to

- [Concept: Cache-first LLM architecture](../concepts/cache-first-llm-architecture.md) — this course's "validate, retry narrowly, observe, fall back safely" list is the deterministic-software half of what that concept's cache layers protect.
- [xingai-learn](../products/xingai-learn.md) — a real, running instance of "typed boundary around an LLM call," at production scale (187-pattern catalog, real cache tables).

## Note on sources

The raw source cites `developers.openai.com/api/docs/guides/function-calling` for OpenAI function calling. This domain looks unusual (most OpenAI docs history lives at `platform.openai.com`) but was verified as a real, resolving primary source via web search on 2026-07-16 — not a typo.

ZH sibling ingested 2026-07-16: Python code block byte-identical, heading count matches (7/7), Mermaid meaning matches.

## Sources

`raw/courses/01-llm-application-engineering.md`
