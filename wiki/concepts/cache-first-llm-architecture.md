# Concept: Cache / Fallback LLM Discipline

Two related goals that show up across courses and the public claims POC:

1. **Bound LLM cost** — don't pay for a model call on every identical or near-identical request when caching or reuse is possible ([Course 01](../courses/01-llm-application-engineering.md) caching module; [Course 06](../courses/06-production-ai-engineering.md) cost-per-task release gates).
2. **Never make one LLM call a single point of failure** — keep a deterministic path so the system still completes when the model is down or returns garbage.

## Public instance: claims-workflow-v2-poc dual-path

[claims-workflow-v2-poc](../products/claims-workflow-v2-poc.md) runs heuristic and LLM paths (`_run_heuristic` / `_run_llm`, gated by `llm_client.is_available()`), falling back to heuristic on any `LLMError`. That is a *fallback*, not a content-hash cache — but it shares the "decision must still complete" discipline Course 06 expects from production systems.

## Taught in miniature

- [Course 01](../courses/01-llm-application-engineering.md) — validate, retry narrowly, observe, fall back safely.
- [Course 06](../courses/06-production-ai-engineering.md) — release-gate thresholds such as `cost_per_task` turn the same goal into a measurable gate.

## Sources

`raw/courses/01-llm-application-engineering.md`, `raw/courses/06-production-ai-engineering.md`, `raw/claims-workflow-v2-poc/` (architecture + ADR-009 Phase 2)
