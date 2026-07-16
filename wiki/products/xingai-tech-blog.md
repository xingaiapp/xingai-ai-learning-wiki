# Product family: xingai-tech-blog (selected)

**Repo:** [xingai-tech-blog](https://github.com/xingaiapp/xingai-tech-blog)

Raw holds nine English posts. This page is **not** that file list — it is what those posts jointly argue that the courses/POCs alone leave implicit.

## Cross-cutting claims (from the selected set)

1. **Decision engine ≠ chatbot** (`2026-07-01-xingai-decision-engine-not-chatbot`) — same pole as Course 07 and the claims "assistant not auto-adjudicator" stance. If the UI is a chat transcript, you probably inverted the product.
2. **MCP is phased, not a big-bang gateway** (`mcp-phased-rollout`, `mcp-architecture-best-practices`) — matches the oauth-vs-coverage split: prove auth on a thin surface, prove coverage on another, combine later ([family synthesis](../syntheses/claims-poc-family-tradeoffs.md)).
3. **Skills vs MCP** (`2026-06-14-cursor-skills-vs-mcp-when-to-use-which`) — different trust and distribution boundaries; Course 04's capability negotiation is MCP-shaped, while agent skills are authoring-time packs. Don't grade one with the other's checklist. Marketing “MCP vs RAG vs Skills” posters that treat them as mutually exclusive fail this test — see [mcp-vs-rag-vs-skills](../syntheses/mcp-vs-rag-vs-skills.md).

4. **Loops beat prompts** (`loop-engineering-enterprise-ai-runtime`, plus design articles) — see [Loop engineering](../concepts/loop-engineering.md).
5. **Worker writes / CQRS** (`cqrs-sqlite-worker-writes`) — rhyme with Course 07's "APIs transport, workers compute." Public teaching post; this wiki still does not ingest private product ADRs it may allude to.
6. **Claims multi-agent writeup** (`2026-06-25-...`) — narrative companion to [claims-multiagent-rag-poc](claims-multiagent-rag-poc.md), not a second source of truth if README and post disagree — prefer the POC tree + ADR.

## Deliberately skipped

Product-changelog posts about private apps (firewall, learn internals, invest digests, radar stacks). Those are public text, but they pull this wiki toward private product archaeology. Prefer courses + POCs + pattern packs.

## Sources

`raw/xingai-tech-blog/posts/` (nine selected files); synthesis across them, not a catalog.
