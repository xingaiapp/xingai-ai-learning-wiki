# ADR-004: Cache-Always Strategy for Real Learning Data

**Date:** 2026-07-14  
**Status:** Accepted  
**Author:** Xing @ XingAI  
**Also available:** [中文](004-cache-always-real-data.zh.md)

## Context

Learn AI is moving from demo seed data toward real pattern/question/company metadata. Public sources such as pattern-based LeetCode lists, open-source solution indexes, and company-frequency datasets can improve the product, but they must not be fetched opportunistically during a user request.

ADR-002 already made the analyze path cache-first for LLM/OCR work. This ADR extends that rule to every real-data source used by Learn AI.

## Decision

Learn AI uses a **cache-always** strategy:

1. **No live external fetch in user request paths.**
   - `/api/questions/analyze`
   - `/api/patterns/graph`
   - `/api/readiness`
   - `/api/companies`
   - dashboard/history/weakness views
2. **External pattern/question/company data is imported offline first.**
   - Importers may read public datasets or curated files.
   - They write normalized rows into SQLite cache/source tables.
   - Runtime engines read only those local rows.
3. **LLM calls remain cache-guarded.**
   - Exact input cache hits return with no LLM call.
   - Cold analyze requests may make one LLM call only after cache miss.
   - Dashboard/readiness/company pages never call the LLM.
4. **Data provenance is required for imported real data.**
   - Store `source_name`, `source_url`, `license_note`, and `imported_at`.
   - If provenance is missing, the row is not eligible for production recommendations.
5. **Insufficient cache beats fake certainty.**
   - If a company profile or pattern cluster is not cached, return an explicit insufficient-data state.
   - Do not invent company weights, readiness multipliers, or pattern frequencies at request time.

## Implementation Requirements

Implemented 2026-07-14:

- [x] `data/pattern_catalog.v1.json` curated source artifact.
- [x] Offline importer script: `scripts/import_patterns.py`.
- [x] Offline refresh wrapper: `scripts/refresh_catalog.py`.
- [x] SQLite source/provenance fields for pattern/question/company metadata.
- [x] DB-first similar-question selection by cached pattern/question metadata.
- [x] Company weights computed from cached `company_pattern_weights`, not hardcoded request-time heuristics.
- [x] Dedicated real-data cache tests: `apps/api/tests/test_real_data_cache.py`.

## Consequences

Positive:

- The product becomes real without making request latency or reliability depend on external websites.
- Recommendations become auditable: every pattern/company signal can point to cached provenance.
- The system can safely use public datasets while respecting licensing and source quality.

Tradeoffs:

- Data may be stale until the importer runs.
- Importers need their own validation and refresh workflow.
- First-run setup becomes more explicit: seed is no longer enough for a production-like local environment.

## Related

- ADR-001: Product Boundary
- ADR-002: One LLM Call, Many Engines
- ADR-003: Decision Ledger Adoption
