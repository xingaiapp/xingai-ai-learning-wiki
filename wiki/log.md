# Log

Append-only. Format: `## [YYYY-MM-DD] ingest|query|lint | <title>`.

## [2026-07-16] ingest | Initial seed — 10 courses + xingai-learn

Copied 20 raw files (10 course READMEs, `courses/README.md`, `COURSE-STANDARD.md`, `xingai-learn/README.md`, ADR-001..007) from `xingai-enterprise-ai-design/courses/` and `xingai-learn/` into `raw/`. Created 10 course pages, 1 product page, 4 concept pages, 2 synthesis pages, `overview.md`, `index.md`. This ingest was seeded directly from a prior review session's findings rather than a cold read, so it includes verified/unverified flags on specific claims from that review (see `syntheses/review-findings-2026-07-16.md`).

## [2026-07-16] lint | Pre-seed review (courses + xingai-learn)

Full findings filed at [syntheses/review-findings-2026-07-16.md](syntheses/review-findings-2026-07-16.md). Summary: courses fully compliant with `COURSE-STANDARD.md`, all code verified by hand, all links (internal + external) verified real, bilingual parity spot-checked and solid. `xingai-learn`: version numbers and "187 patterns" claim verified accurate; one stale-looking cross-reference in ADR-001 was found, "fixed" incorrectly on the first attempt (assumed the wrong target repo), then fixed correctly after a workspace-wide grep surfaced the actual (external, not locally checked-out) repo it referred to.

## [2026-07-16] query | "there are 2 learn course in this workspace"

Answered as a synthesis, not a one-off chat reply — filed as [syntheses/courses-vs-xingai-learn-boundary.md](syntheses/courses-vs-xingai-learn-boundary.md). Verdict: not duplicates, no consolidation needed; flagged an unbuilt cross-link opportunity (ADR-001 → Course 09) as a possible future ingest, not done in this pass.

## [2026-07-16] ingest | Course ZH siblings + three more products

Expanded the wiki on request ("继续往里面 ingest"). Added: (1) all 10 courses' `.zh.md` + `courses/README.zh.md` + `COURSE-STANDARD.zh.md` — parity checked programmatically (Python code blocks diffed, heading counts compared) rather than by eye; found one real diff (Course 07's `api_view()` inline comment is localized, correctly, not a parity break) and confirmed the rest byte-identical on code. (2) `claims-workflow-v2-poc` (README, `PRODUCTION-READINESS.md`, `architecture.md`, ADR-008, ADR-009) — new page `products/claims-workflow-v2-poc.md`, now the most cross-referenced entity in the wiki. (3) `xingai-agent-firewall` (README, PRD, ADR-001..006) — new page `products/xingai-agent-firewall.md`; read ADR-002 and ADR-004 in full to get the deterministic-scoring and session-taint mechanisms right rather than summarizing from the README alone. (4) This session's own `xingai-opportunity-radar` output (the issue, Decision Card, Content Pack, `portfolio.yaml`) — new page `products/opportunity-radar.md`. Updated every existing page that had referenced these products as plain text to link to the new pages instead. Re-ran the link-check script after all edits — see the corresponding lint entry below if any breaks were found.
