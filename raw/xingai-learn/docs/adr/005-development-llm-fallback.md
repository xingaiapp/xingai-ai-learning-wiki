# ADR-005: Development-only LLM Fallback

**Date:** 2026-07-14  
**Status:** Accepted  
**Author:** Xing @ XingAI  
**Also available:** [中文](005-development-llm-fallback.zh.md)

## Context

Learn AI should be a real learning decision system, not a mock-data demo. At the same time, local development often runs with missing, expired, or network-blocked OpenAI credentials. If cold analyze requests always fail in that case, engineers cannot test the UI, Decision Ledger writes, DB-first similar questions, or company-mode weighting.

ADR-004 already requires real pattern/question/company data to come from cached metadata. This ADR covers only the LLM analyze path in local development.

## Decision

Add a **development-only deterministic LLM fallback**:

1. When `APP_ENV=development` and `ALLOW_MOCK_LLM_FALLBACK=true`, OpenAI authentication/network/API failures may fall back to `_mock_response()`.
2. The fallback is only for local testing of the product flow.
3. Production and non-development environments must re-raise OpenAI errors instead of silently returning fallback analysis.
4. Health output exposes whether fallback is enabled through `llm_fallback_enabled`.
5. Real metadata remains cache-first and DB-backed; fallback does not fetch external data or change pattern/company cache semantics.

## Consequences

Positive:

- Local testing can continue even when the copied test key is invalid or the network is unavailable.
- The UI, catalog cache, company weights, and Decision Ledger can be tested end-to-end.
- Production behavior remains honest: broken credentials produce errors instead of fake analysis.

Tradeoffs:

- Local fallback analysis is deterministic and incomplete. It must not be used as quality evidence.
- Engineers must check `llm_fallback_enabled` before judging analysis quality.
- Any production deployment should set `APP_ENV` away from `development` and should not rely on fallback.

## Implementation

- Config: `apps/api/app/config.py`
- LLM wrapper: `apps/api/app/services/llm.py`
- Health signal: `apps/api/app/main.py`

## Related

- ADR-002: One LLM Call, Many Engines
- ADR-004: Cache-Always Strategy for Real Learning Data
