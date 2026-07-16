# ADR-002: One LLM Call, Many Engines — Cache-First in the Request Path

**Date:** 2026-07-05
**Status:** Accepted
**Author:** Xing @ XingAI
**Also available:** [中文](002-single-call-engines.zh.md)

## Context

The XingAI global standard says: all logic in a worker, FastAPI reads cache only, frontend renders cache. That standard assumes the input space is enumerable — a worker can precompute scores for N stocks or M meal plans on a schedule.

Learn AI's input space is unbounded: any interview question, typed or screenshotted, at the moment the user pastes it. There is nothing to precompute before the user arrives. A background worker would add a queue, a polling UI, and operational surface without removing a single LLM call.

Separately, the analysis itself decomposes into many concerns (classification, interviewer intent, prerequisites, pattern mapping, solution, replay steps, similar questions, recommendation). The naive design is one LLM call per engine — nine calls per question.

## Decision

Two coupled choices, both visible in `apps/api/app/engines/decision.py`:

**1. One LLM call, many engines.** A single analysis call (prompt in `agents/prompts/analyze.md`) returns one JSON document; the engines (`classification`, `intent`, `prerequisites`, `pattern_engine`, …) are *parsers and post-processors* over that document, not independent LLM callers. Only the engines that need the database — similar questions, company-aware recommendation, readiness — do their own work, against SQLite, with zero extra LLM calls.

**2. LLM in the request path, guarded by three cache layers.** No worker process. `run_decision_pipeline` is synchronous and cache-first (`apps/api/app/cache.py`, tables in `models.py`):

| Layer | Table | Key | Saves |
|---|---|---|---|
| OCR | `input_cache` | sha256(image) | vision call on re-uploaded screenshots |
| Analysis | `analysis_cache` | hash(text + image hash) | the full analyze call on repeat questions |
| Similar questions | `similar_question_cache` | category:subcategory:pattern | per-pattern regeneration (5 served from 20 cached) |

A cache hit serves the entire response with no LLM involvement; a miss pays exactly one analysis call and writes the cache for everyone after.

This is a deliberate, documented deviation from the worker standard, in the same spirit as Meal AI's Next.js API-route ledger (blog 2026-07-03): the standard's *goal* is "no LLM call on every page load," and cache-first achieves that goal where precompute cannot.

## Consequences

Positive:
- Cost is bounded by *distinct* questions, not traffic. Popular questions (the common case in interview prep) are one-time costs.
- Nine engines stay independently testable as pure functions over a JSON document — no nine-call latency or nine-way failure modes.
- No queue/worker infrastructure to operate at MVP scale.

Tradeoffs:
- Cold-miss latency is the full LLM round trip, felt by the user in the analyze flow. Acceptable for an analysis tool; unacceptable if this ever becomes a dashboard — that page must read cache tables only.
- One big analysis prompt is a single point of quality: a schema change in the JSON touches every parser. Mitigation: parsers live in one module each with defaults (`raw.get(...)`), and the prompt file is versioned in `agents/prompts/`.
- SQLite in the API process ties us to one machine. Fine at current scale; the migration trigger is concurrent-writer errors or multi-region deploy.

## Alternatives Considered

| Option | Reason rejected |
|---|---|
| Worker + queue per the global standard | Precompute impossible for unbounded input; adds polling UX and infra with no cost savings. |
| One LLM call per engine | ~9× cost and latency per cold question; cross-engine consistency (classification vs. pattern) becomes a prompt-alignment problem. |
| No cache, always call | Repeat questions are the norm in interview prep; would pay per page view — exactly what the standard forbids. |

## Related

- [ADR-001: Product Boundary](./001-product-boundary.md)
- [ADR-003: Decision Ledger Adoption](./003-decision-ledger.md)
- xingai-engineering-system: `patterns/cache-first-before-llm.md`, `patterns/worker-cache-boundary.md`, `patterns/product-upgrade-rule.md`
