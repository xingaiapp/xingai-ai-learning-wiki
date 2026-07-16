# Synthesis: 2026-07-16 Courses Review Findings

Audit trail from the review that seeded this wiki — filed as a page instead of left in chat. Scope here is the **public curriculum** only.

## What was checked

- All 10 courses against `COURSE-STANDARD.md`'s required structure (5W+How, code, Mermaid diagram, failure analysis, lab/interview gate, sources).
- Every code example, by hand: `cosine`, `recall_at_k`, `precision_recall`, `opportunity_score`, `release_allowed`, `transition`, `parse_triage`, `TOOL["inputSchema"]` assertions — all correct.
- Bilingual parity — spot-checked Course 00 and Course 04 plus top-level course index ZH — faithful, structurally matched translations.
- Internal cross-references the courses make (`guides/`, `articles/`, `assessments/`, `capstones/`, `interview-bank/`, `deep-enterprise-ai/`, and sibling-repo paths named in References) — resolve in the public design / POC trees where applicable.
- External URLs that looked unusual: `developers.openai.com/...`, `a2a-protocol.org/...`, `modelcontextprotocol.io/specification/2025-11-25/...` — verified real via web search.

## What was found

No curriculum structure or sample-code defects that required a fix in the courses themselves on that pass. ZH parity had one intentional comment localization in Course 07 (`api_view()`), correctly treated as localization rather than a parity break.

## Lesson for Lint

"Not present in this local workspace" is not evidence a cited public URL or public repo path is wrong — check the remote before calling a cross-reference stale. Conversely, for this **public** wiki: presence of a private sibling checkout locally is not a license to ingest it.

## Sources

This session's chat history (2026-07-16) over public `xingai-enterprise-ai-design/courses/` and public POC docs; see `raw/courses/` and `raw/claims-workflow-v2-poc/`.
