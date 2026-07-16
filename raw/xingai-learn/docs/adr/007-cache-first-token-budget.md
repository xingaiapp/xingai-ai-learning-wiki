# ADR-007: Aggressive Cache-First to Minimize LLM Token Spend

**Date:** 2026-07-14  
**Status:** Accepted  
**Also available:** [中文](007-cache-first-token-budget.zh.md)

## Context

Learn AI must analyze unbounded interview questions, so some LLM use is unavoidable. Token cost still has to stay near zero for normal study: the same problems, patterns, and screenshots get revisited constantly.

## Decision

Always prefer cache over model. LLM is cold-miss only.

| Layer | When | Tokens |
|---|---|---|
| Browser `sessionStorage` | Identical analyze text+locale in the same tab session | 0 |
| OCR `input_cache` | Same image bytes (sha256) | 0 vision |
| Analysis `analysis_cache` | Stable fingerprint (title+pattern slug+locale, or normalized body) | 0 |
| Title alias hash | Same analysis title + locale under a different prompt shell | 0 |
| Prior `questions.analysis_json` reuse | Same Problem title seen before | 0 |
| Catalog similar-questions | DB only (never LLM) | 0 |
| Mock / `FORCE_MOCK_LLM` | No key or budget lock | 0 |
| OpenAI analyze | True cold miss only; truncated user text; compact system prompt; `max_tokens` cap | paid once |

Fingerprints ignore ephemeral practice-prompt lines (Source URL, “Teach this…”, locale coaching) so small UI churn does not miss the cache.

TTLs default to ~1 year (`ANALYSIS_CACHE_TTL_HOURS=8760`). Seed runs `prewarm_cache` for Edit Distance / Course Schedule / Two Sum so demos never bill.

## Consequences

- Repeat Analyze clicks and Study Tree → Analyze flows are effectively free after the first hit.
- Changing solution schema still uses `sol:v2` in the fingerprint so quality upgrades bust intentionally.
- Forcing `FORCE_MOCK_LLM=true` in production-like staging keeps spend at zero while UI is tested.

## Related

- [ADR-002: One LLM Call, Many Engines](./002-single-call-engines.md)
- [ADR-004: Cache-Always Real Data](./004-cache-always-real-data.md)
