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

## [2026-07-16] lint | Bilingual wiki rule in skills + AGENTS

`xingai-wiki-ingest` and `xingai-ai-learning-wiki` now require EN+中文 (`name.md` + `name.zh.md`) on every new/updated wiki content page in the same ingest pass. Lint: bilingual audit. `wiki/log.md` remains English-only. Existing EN-only pages are debt — backfill on next touch or dedicated pass.

## [2026-07-16] ingest | external: LLM vs RAG vs AI Agent vs Agentic AI (image)

User-attached Michael Lee “Layers of Intelligence” poster (Language→Grounding→Execution→Orchestration + foundation strip). Package: `raw/external/2026-07-16-llm-rag-agent-agentic-layers/`. Wiki: [syntheses/llm-rag-agent-agentic-vs-xingai.md](syntheses/llm-rag-agent-agentic-vs-xingai.md) · [中文](syntheses/llm-rag-agent-agentic-vs-xingai.zh.md). `verified: partial`. Critique: “vs” false exclusivity; MCP only under Agentic; foundation tiles help vs six-ring poster but still miss two-wall auth / Decision Ledger; distinct from Classical stack and MCP|RAG|Skills cuts. Linked from Course 00 + sibling syntheses; index EN+ZH updated.

## [2026-07-16] lint | Bilingual backfill (all wiki content)

Dedicated pass: every `wiki/` content page now has a `.zh.md` peer (31/31), plus root `README.zh.md` / `AGENTS.zh.md` / `DISCLAIMER.zh.md`. EN pages carry `Chinese:` headers; ZH pages carry `English:`. Internal links in ZH point at `.zh.md` siblings. Syntheses + products + remaining concepts translated in this pass; courses/index/overview had already been started earlier the same day. `wiki/log.md` stays EN-only.

## [2026-07-16] lint | Drop third-party-authored image wiki

Removed wiki + `raw/external/` for images with non-XingAI author credits:

- Michael / Michael Lee (From Pilots to Platforms): `layers-of-ai`, `llm-rag-agent-agentic-layers`
- Rishi: `enterprise-ai-agent-architecture`

Deleted synthesis pages (EN+ZH) and scrubbed links from index, Course 00, loop-engineering, agent-governance, mcp-vs-rag-vs-skills. **Kept** `mcp-vs-rag-vs-skills` (no author line on crop — not clearly third-party-attributed).

## [2026-07-16] lint | UX PNG rule in skills + AGENTS

Both Cursor skills (`xingai-ai-learning-wiki`, `xingai-wiki-ingest`) and `AGENTS.md` / `AGENTS.zh.md` now require embedding XingAI UX PNGs under `wiki/assets/ux/<slug>/` when chrome/flow/theme/demo visuals are needed (EN+ZH same path). Shared detail: `~/.cursor/skills/xingai-wiki-ingest/references/ux-png.md`. Still refuse third-party-authored marketing posters.

## [2026-07-16] ingest | external: RAG vs Agentic RAG (image)

Unattributed three-panel poster (Standard RAG / AI Agent / Multi-Agent RAG + MCP Servers). Package: `raw/external/2026-07-16-rag-vs-agentic-rag/`. Wiki: [syntheses/rag-vs-agentic-rag-vs-xingai.md](syntheses/rag-vs-agentic-rag-vs-xingai.md) · [中文](syntheses/rag-vs-agentic-rag-vs-xingai.zh.md). `verified: partial`. Ownership gate: no clear non-XingAI author → critique ingest OK (not UX). Critique: “vs” false exclusivity; middle panel is tool-agent not grounded RAG; Multi-Agent MCP without auth walls; Vector Db assumed. Linked from Course 02 + mcp-vs-rag-vs-skills; index EN+ZH updated.




## [2026-07-16] ingest | external: OAuth/OIDC/Azure Identity/API Security outline

User-owned teaching outline (Cursor paste). Package: `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/` (`SOURCE.md` verified: yes; `content.md` digest + catalog). Wiki: 26 bilingual concept pages + hub under `wiki/concepts/oauth-oidc-azure-identity/` (00-overview … 26-complete-azure-reference-architecture). Synthesis bar: each page Known/Missing/Rethink/Debate/Needs evidence; Azure pages framed as teaching maps not XingAI production claims; cross-links to claims-mcp-oauth-poc, Course 04, agent-governance, design OAuth/PKCE articles. No UX PNG (theory track). Index EN+ZH + agent-governance EN+ZH updated.

## [2026-07-16] sync | P1 tech-blog teaching slice + OAuth catalog lint

`gh` org list forbidden in this environment — sync used **local public clones** only (design/pocs/engineering-system/tech-blog).

- **OAuth catalog:** `wiki/concepts/oauth-oidc-azure-identity/` — 27 EN + 27 ZH; epistemic headers pass; still uncommitted from prior ingest.
- **Design articles:** local vs raw — no missing EN article filenames.
- **Tech blog:** raw had 9 EN posts; copied 17 priority EN+ZH teaching peers (MCP auth, PKCE, scope≠policy, Robinhood fail-closed, agent-firewall, decision ledger, Learn AI cache) → raw now 43 md files. Updated [products/xingai-tech-blog](products/xingai-tech-blog.md) · [中文](products/xingai-tech-blog.zh.md) with claims 7–9 + OAuth catalog link. Index raw note updated.
- **Skipped:** full 75-post mirror; private-product changelog archaeology; `xingai-dot-app` P2; self-ingest.
- **UX:** no new chrome pages this pass → no UX PNG adds.
- **Push:** not requested.

## [2026-07-16] lint | bilingual + epistemic (oauth + tech-blog page)

OAuth tree epistemic section parity OK. Tech-blog product page EN+ZH rewritten with Known/Missing/Rethink/Debate/Needs evidence. No private-repo dumps introduced.

## [2026-07-16] docs-pack | Engineering Communication Coach

Created ADR-002 / tech-blog / enterprise design for skill-curriculum + ledger pattern (see those repos). **Skipped** wiki `products/engineering-coach` page: GitHub API 404 for the coach repo → treat as non-public for wiki dumps; public teaching stays via blog + design URLs + xingai.app catalog. Snapshotted new blog (+ design article) into `raw/`. Also pushing pending OAuth catalog + prior tech-blog teaching slice from earlier sync.

## [2026-07-16] course | Course 10 OAuth/OIDC/Azure Identity

Published specialization Course 10 in `xingai-enterprise-ai-design` (26 bilingual modules + hub). Added wiki course pages `wiki/courses/10-oauth-oidc-azure-identity(.zh).md`, linked from index and concept overview.

## [2026-07-16] lint/ingest | oauth-oidc-azure-identity ← Course 10

Rewrote `wiki/concepts/oauth-oidc-azure-identity/` (overview + 26 EN/ZH pages) from Course 10 teach blocks + epistemic critique. Snapshotted course into `raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/`. External outline retained only as provenance. Updated course wiki Known + index blurbs.
