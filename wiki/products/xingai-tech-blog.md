# Product family: xingai-tech-blog (selected)

Chinese: [xingai-tech-blog.zh.md](xingai-tech-blog.zh.md)

**Repo:** [xingai-tech-blog](https://github.com/xingaiapp/xingai-tech-blog)

Raw holds a **selected** teaching set (not the full public blog). This page is **not** that file list — it is what those posts jointly argue that the courses/POCs alone leave implicit.

## Cross-cutting claims (from the selected set)

1. **Decision engine ≠ chatbot** (`2026-07-01-xingai-decision-engine-not-chatbot`) — same pole as Course 07 and the claims "assistant not auto-adjudicator" stance. If the UI is a chat transcript, you probably inverted the product.
2. **MCP is phased, not a big-bang gateway** (`mcp-phased-rollout`, `mcp-architecture-best-practices`) — matches the oauth-vs-coverage split: prove auth on a thin surface, prove coverage on another, combine later ([family synthesis](../syntheses/claims-poc-family-tradeoffs.md)).
3. **Skills vs MCP** (`2026-06-14-cursor-skills-vs-mcp-when-to-use-which`) — different trust and distribution boundaries; Course 04's capability negotiation is MCP-shaped, while agent skills are authoring-time packs. Don't grade one with the other's checklist. Marketing “MCP vs RAG vs Skills” posters that treat them as mutually exclusive fail this test — see [mcp-vs-rag-vs-skills](../syntheses/mcp-vs-rag-vs-skills.md).
4. **Loops beat prompts** (`loop-engineering-enterprise-ai-runtime`, plus design articles) — see [Loop engineering](../concepts/loop-engineering.md).
5. **Worker writes / CQRS** (`cqrs-sqlite-worker-writes`) — rhyme with Course 07's "APIs transport, workers compute." Public teaching post; this wiki still does not ingest private product ADRs it may allude to.
6. **Claims multi-agent writeup** (`2026-06-25-...`) — narrative companion to [claims-multiagent-rag-poc](claims-multiagent-rag-poc.md), not a second source of truth if README and post disagree — prefer the POC tree + ADR.
7. **Scope is not policy** (`2026-07-13-mcp-auth-scope-is-not-policy-second-wall`, `mcp-oauth-vs-api-key`, `mcp-auth-api-key-vs-oauth-pkce`) — wall #1 (OAuth) vs wall #2 (business rules). Maps to [agent-governance-and-mcp](../concepts/agent-governance-and-mcp.md) and the longer [OAuth / OIDC / Azure Identity catalog](../concepts/oauth-oidc-azure-identity/00-overview.md).
8. **Fail-closed MCP gateways** (`2026-07-11-robinhood-mcp-gateway-fail-closed`, related ADR posts) — default deny for consequential tools; human-in-the-loop is part of the protocol, not an afterthought.
9. **Decision Ledger as cross-product memory** (`meal-ai-nextjs-decision-ledger`, `learn-ai-real-pattern-cache-decision-ledger`, decision-engine ledger posts) — see [decision-ledger-pattern](../concepts/decision-ledger-pattern.md).

## Known

- Selected posts in `raw/xingai-tech-blog/posts/` were expanded 2026-07-16 with July MCP-auth / ledger / firewall teaching articles (EN+ZH peers when present).
- Claims above are grounded in those filenames; open a post under raw before quoting numbers or APIs.

## Missing

- Full blog corpus (~75 EN posts) is **not** mirrored — only teaching-priority slices.
- Private-product changelog posts remain deliberately out of wiki synthesis.

## Rethink

- Treating the tech blog as a second README for every POC duplicates noise; prefer POC + ADR, use blog for the *argument*.

## Debate

- How many firewall / Robinhood posts belong in this learning wiki vs staying blog-only (security depth vs scope creep).

## Needs evidence

- Whether every selected post still matches the current public POC README after later POC commits.

## Deliberately skipped

Product-changelog posts about private apps (invest digests, radar stacks, unpublished internals). Prefer courses + POCs + pattern packs.

## Sources

`raw/xingai-tech-blog/posts/` (selected files); synthesis across them, not a catalog.
