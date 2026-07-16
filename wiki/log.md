# Log

Append-only. Format: `## [YYYY-MM-DD] ingest|query|lint | <title>`.

## [2026-07-16] ingest | Initial seed — 10 courses + claims POC + (later removed) private trees

Originally copied course READMEs from public `xingai-enterprise-ai-design/courses/` and also private product trees. Created course pages, concept pages, synthesis pages, `overview.md`, `index.md`. Later the same day, private trees were removed — see the lint entry below.

## [2026-07-16] lint | Courses review (public curriculum)

Full findings filed at [syntheses/review-findings-2026-07-16.md](syntheses/review-findings-2026-07-16.md). Summary: courses compliant with `COURSE-STANDARD.md`, sample code checked by hand, internal + external links verified, bilingual parity spot-checked.

## [2026-07-16] ingest | Course ZH siblings + claims-workflow-v2-poc

Added all 10 courses' `.zh.md` + course index ZH + `COURSE-STANDARD.zh.md` — parity checked programmatically (Python code blocks diffed, heading counts compared). Found one intentional localization (Course 07 `api_view()` comment). Ingested public `claims-workflow-v2-poc` (README, `PRODUCTION-READINESS.md`, `architecture.md`, ADR-008, ADR-009) as `products/claims-workflow-v2-poc.md`.

## [2026-07-16] lint | Public-repo scrub

Removed all `raw/` and `wiki/` material sourced from private XingAI repos. Rewrote README, AGENTS.md, index, overview, concepts, course cross-links, and review synthesis so this public wiki only carries public curriculum + public POC knowledge. Rule now encoded in AGENTS.md: ingest public sources only.
