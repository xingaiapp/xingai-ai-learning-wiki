# Product: xingai-learn ("Learn AI")

**Live at:** learn.xingai.app · **Version at last check (2026-07-16):** 0.3.17 · **Repo:** `xingai-learn`

**"Master Patterns. Not Questions."** An AI Interview Decision System — takes a coding-interview question (text or screenshot), classifies it into a pattern/family knowledge graph, and answers "what should I practice next?" This is a **general coding-interview pattern trainer** (two pointers, sliding window, DP, graph traversal — 187 curated patterns across 16 families), not an AI-engineering-specific product. See [wiki/syntheses/courses-vs-xingai-learn-boundary.md](../syntheses/courses-vs-xingai-learn-boundary.md) for why this matters — it's easy to conflate with [Course 09](../courses/09-ai-interview-mastery.md) by name alone.

## Architecture

`Frontend (Next.js 15) → FastAPI → Engines → SQLite`. Nine engines (Classification, Intent, Prerequisite, Pattern, Solution+Replay, Similar Question Cache, Recommendation, Decision) run as **parsers over one LLM analysis call**, not nine separate LLM calls — see [ADR-002](#adr-002-one-llm-call-many-engines) below. This is the same "typed boundary around a model call" discipline [Course 01](../courses/01-llm-application-engineering.md) teaches, at production scale.

## ADRs (verified against files on disk, 2026-07-16)

- **ADR-001: Product Boundary** — Learn AI vs. Research AI vs. SAT AI: three separate products/repos, no shared code at v1, sharing *patterns not libraries*. **This wiki fixed a stale cross-reference in this ADR** — see [Review Findings](../syntheses/review-findings-2026-07-16.md).
- **ADR-002: One LLM Call, Many Engines** — see [Concept: Cache-first LLM architecture](../concepts/cache-first-llm-architecture.md); this ADR is the canonical writeup of that concept.
- **ADR-003: Decision Ledger Adoption** — see [Concept: Decision Ledger pattern](../concepts/decision-ledger-pattern.md).
- **ADR-004: Cache-Always Strategy for Real Learning Data** — no dashboard/readiness/company/pattern-graph request may fetch external data or invent weights at request time; everything is imported offline into SQLite first.
- **ADR-005: Development-only LLM Fallback**, **ADR-006: SQLite Runtime Schema Guard Before Alembic**, **ADR-007: Cache-First Token Budget** — operational hardening around the same cache-first core (`FORCE_MOCK_LLM=true` spends $0; seed prewarms common demos).

## Verified claims (checked against actual data, 2026-07-16)

- **"187 patterns" is accurate** — `data/pattern_catalog.v1.json`'s `pattern_count` field says 187, and summing every family's question list independently also totals 187. No discrepancy.
- **Company Mode's "Google, Meta, Amazon, etc."** — the catalog has exactly 4 companies (Google, Meta, Amazon, OpenAI), each with a real `pattern_weights` list (not empty, as an earlier wrong key-name probe briefly suggested before the correct field name was found).
- **Version consistency** — `VERSION` (0.3.17), `package.json` (0.3.17), and the top entry of `README.md`'s version history all agree.

## Connects to

- [Concept: Cache-first LLM architecture](../concepts/cache-first-llm-architecture.md)
- [Concept: Decision Ledger pattern](../concepts/decision-ledger-pattern.md)
- [Course 01](../courses/01-llm-application-engineering.md), [Course 09](../courses/09-ai-interview-mastery.md)
- `xingai-research-ai` (Research AI, `research.xingai.app`, "Learning Decision System") and `xingai-research-startup-agent` (a *different*, separately-named GitHub repo — see Review Findings) are the two sibling products ADR-001 draws the boundary against.

## Sources

`raw/xingai-learn/README.md`, `raw/xingai-learn/docs/adr/001..007-*.md`
