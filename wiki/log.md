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

## [2026-07-16] ingest | Full public-repo sync (skill: xingai-ai-learning-wiki)

Scanned 6 public `xingaiapp` repos via `gh`. **Ingested/refreshed:**

- `xingai-enterprise-ai-design` — remirrored `courses/` to living folder layout; snapshotted all articles + guides; assessments + deep-enterprise-ai READMEs
- `xingai-enterprise-ai-pocs` — all 6 POCs under `raw/pocs/` + ADRs 001–009
- `xingai-engineering-system` — 8 AI patterns + ADR-002
- `xingai-tech-blog` — 9 architecture teaching posts (EN)

**Skipped:** `xingai-ai-learning-wiki` (self), `xingai-dot-app` (P2 marketing), private repos, product-changelog blog posts about private apps.

**Wiki updates:** product pages for every public POC + design/engineering/blog hubs; new concept `loop-engineering`; remapped Sources paths; expanded index/overview/README.

## [2026-07-16] lint | Post-sync

Checked: no `raw/` trees for known-private product repos; wiki product pages only reference public GitHub URLs / `raw/pocs|courses|xingai-*` public snapshots; fixed stale relative sibling link in Course 02. Remaining intentional pointers: public course index may name Learn AI by URL; Course 07 may cite a private ADR path without ingesting it.

## [2026-07-16] lint | Synthesis bar (anti copy-paste)

Raised the bar in `AGENTS.md` + global skill: wiki pages must add contrasts/tensions, not shortened READMEs or file catalogs. Rewrote thin product family pages; added [syntheses/claims-poc-family-tradeoffs.md](syntheses/claims-poc-family-tradeoffs.md) as the multi-POC answer that no single raw file contains.

## [2026-07-16] ingest | external: Layers of AI (image)

User-attached infographic (Classical→ML→NN→DL→GenAI→Agentic). Package: `raw/external/2026-07-16-layers-of-ai/` (SOURCE.md, notes.md, assets/layers-of-ai.png). Wiki: new [syntheses/layers-of-ai-vs-curriculum.md](syntheses/layers-of-ai-vs-curriculum.md); Course 00 Connects-to updated. `verified: partial` (visual labels only; no canonical URL).

## [2026-07-16] lint | Epistemic standard added to skills + AGENTS

Updated `xingai-wiki-ingest` and `xingai-ai-learning-wiki` skills plus `AGENTS.md`: every wiki write must cover Known / Missing / Rethink / Debate / Needs evidence; no guessing as fact. Checklist at `~/.cursor/skills/xingai-wiki-ingest/references/epistemic-checklist.md`. Rewrote layers-of-ai synthesis into that shape as the template example.

## [2026-07-16] ingest | external: Enterprise AI Agent Architecture (image)

User-attached Rishi reference poster (orchestration→ops). Package: `raw/external/2026-07-16-enterprise-ai-agent-architecture/`. Wiki: [syntheses/enterprise-agent-architecture-vs-xingai.md](syntheses/enterprise-agent-architecture-vs-xingai.md); linked from loop-engineering + agent-governance. `verified: partial`. Critique focus: guardrails-after-RESPOND vs gate-before-ACT; Missing two-wall auth / Decision Ledger / MCP on poster; Missing full LLMOps in public POCs.

## [2026-07-16] ingest | external: MCP vs RAG vs Skills (image)

Three-column marketing architecture poster. Package: `raw/external/2026-07-16-mcp-vs-rag-vs-skills/`. Wiki: [syntheses/mcp-vs-rag-vs-skills.md](syntheses/mcp-vs-rag-vs-skills.md). Grounded against `raw/xingai-tech-blog/posts/2026-06-14-cursor-skills-vs-mcp-when-to-use-which.md` (“Skills teach procedure. MCP grants capability.”). `verified: partial`. Rethink: “vs” implies false exclusivity; Skills column conflates SKILL.md with runtime tools.

