# Concept: Cache-First LLM Architecture

The pattern of putting an LLM call in the request path (because the input space is unbounded and nothing can be precomputed) while still honoring the spirit of "no LLM call on every page load" — not by banning the call, but by guarding it with cache layers keyed on content hashes, so *repeat* inputs never re-pay the call.

## Canonical instance: xingai-learn ADR-002

"One LLM call, many engines": a single analysis call returns one JSON document; nine engines are parsers/post-processors over it, not nine independent callers. Three cache layers (OCR by image hash, full analysis by text+image hash, similar-questions by pattern key) mean cost is bounded by *distinct* questions, not traffic. Explicitly framed as a **deliberate, documented deviation** from the XingAI global standard's worker/cache-only rule — the standard's goal (bounded LLM cost) is achieved differently because the input space can't be enumerated in advance.

## Same instinct, different shape, elsewhere

- [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.md)'s LLM dual-path (`_run_heuristic` / `_run_llm`, gated by `llm_client.is_available()`) isn't a cache — it's a *fallback*, not a cost-saving cache layer — but it shares the same discipline of never letting an LLM call become a single point of failure for a decision that must still complete.
- [Course 06](../courses/06-production-ai-engineering.md)'s release-gate thresholds (`cost_per_task <= 0.08`) are the generalized, metric-based version of the same "bound the cost" goal ADR-002 solves architecturally.
- [Course 01](../courses/01-llm-application-engineering.md)'s "caching" module item is this concept taught in miniature, before xingai-learn's three-layer version generalizes it.

## Sources

`raw/xingai-learn/docs/adr/002-single-call-engines.md`, `raw/xingai-learn/docs/adr/004-cache-always-real-data.md`, `raw/xingai-learn/docs/adr/007-cache-first-token-budget.md`
