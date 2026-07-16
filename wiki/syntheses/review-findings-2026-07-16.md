# Synthesis: 2026-07-16 Review Findings

The audit trail from the review that seeded this wiki — filed as a page instead of left in chat history, per this wiki's own operating principle.

## What was checked

- All 10 courses against `COURSE-STANDARD.md`'s required structure (5W+How, code, Mermaid diagram, failure analysis, lab/interview gate, sources).
- Every code example, by hand: `cosine`, `recall_at_k`, `precision_recall`, `opportunity_score`, `release_allowed`, `transition`, `parse_triage`, `TOOL["inputSchema"]` assertions — all correct.
- Bilingual parity — spot-checked Course 00 and Course 04 (the most complex, with a sequence diagram + code) plus the top-level `courses/README.zh.md` — faithful, structurally matched translations, not abbreviations.
- Every internal cross-reference the courses make (`guides/2026-07-12-mcp-oauth-pkce-lab.md`, four `articles/*.md` paths, `assessments/`, `capstones/`, `interview-bank/`, `deep-enterprise-ai/`, and one cross-repo link into `xingai-invest-ai/docs/adr/012-*.md`) — all resolve, in both languages.
- External URLs that looked unusual enough to doubt: `developers.openai.com/...`, `a2a-protocol.org/...`, `modelcontextprotocol.io/specification/2025-11-25/...` — all verified real via web search, not typos.
- `xingai-learn`'s README claims against actual data: "187 patterns" (verified exact match against `data/pattern_catalog.v1.json`), version numbers across `VERSION`/`package.json`/README changelog (all agree), ADR list on disk vs. README's list (matches).

## What was found wrong, and the fix

**`xingai-learn/docs/adr/001-product-boundary.md`'s Related section** cited "xingai-research-startup-agent ADR-001" as backing for "the same boundary discipline applied to research products."

First pass: assumed this meant the local `xingai-research-ai` folder (the only "research" product folder actually present in this workspace), found its real ADR-001 is titled "Learning Decision System" — a different topic — and "corrected" the reference to point at `xingai-opportunity-radar/config/portfolio.yaml` instead.

**That first pass was itself wrong.** A grep across the workspace surfaced `xingai-tech-blog/posts/2026-07-03-research-startup-agent-four-artifact-pipeline.md`, which cites a real, differently-named GitHub repo: `github.com/xingaiapp/xingai-research-startup-agent` — a "URL → insight → startup idea → PRD → build prompt" pipeline, genuinely distinct from `xingai-research-ai` (`research.xingai.app`, "Learning Decision System"). The original ADR-001 reference was very likely correct all along; it just points at a repo not checked out in this local workspace, which isn't the same as the repo not existing.

**Final fix:** restored the `xingai-research-startup-agent` reference, added the disambiguating note that it's distinct from `xingai-research-ai`, and — since its content genuinely couldn't be verified locally — added an honest flag that it needs confirmation rather than asserting either that it's right or wrong. Applied to both `.md` and `.zh.md`.

**Lesson for this wiki's own Lint operation:** "not present in this local workspace" is not evidence of "doesn't exist" — cross-repo references need a second check (does *anything* else in the workspace corroborate the referenced repo/URL is real?) before being called stale. This session's first-pass mistake is exactly the kind of error the wiki's Lint operation ([AGENTS.md](../../AGENTS.md)) should catch on a future pass over any new cross-repo citation.

## The Opportunity Radar Decision Card (same session, same day)

Separately, this session also ran a XingAI Opportunity Radar issue (2026-07-16) through to a Decision Card and Content Pack: picked **Agent Skill Assurance & Evaluation** as an upgrade to [xingai-agent-firewall](../products/xingai-agent-firewall.md) (not a new repo), rejecting Research Experiment OS, SAT Teacher & Tutor Platform, and Decision Memory Engine on record with reasons (sequencing, not merit, in the first two cases). Full writeup, now ingested: [products/opportunity-radar.md](../products/opportunity-radar.md). Relevant to this wiki because it's the real-world instance of [Course 08](../courses/08-ai-leadership-cto.md)'s portfolio-scoring discipline, and because the pick itself closes the runtime-vs-pre-production gap described in [Concept: Agent governance and MCP](../concepts/agent-governance-and-mcp.md).

## Sources

This session's chat history (2026-07-16), `raw/xingai-learn/docs/adr/001-product-boundary.md` (post-fix), and cross-workspace greps not captured in any single raw file.
