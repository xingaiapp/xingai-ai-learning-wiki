# Synthesis: MCP vs RAG vs Skills (poster) vs XingAI map

Chinese: [mcp-vs-rag-vs-skills.zh.md](mcp-vs-rag-vs-skills.zh.md)

Three-column infographic (user-ingested 2026-07-16): MCP | RAG | Agent Skills as “architectures that improve AI agents.”

Asset: `raw/external/2026-07-16-mcp-vs-rag-vs-skills/`.

## Known

- Poster structure (visual, `verified: partial`): see `notes.md` — MCP host/client/server with external apps; RAG embed→vector DB→augment prompt→generate; Skills host + skill manager + local/dev tools + `SKILL.md` / actions.
- XingAI public teaching already separates **procedure vs capability**:
  - `raw/xingai-tech-blog/posts/2026-06-14-cursor-skills-vs-mcp-when-to-use-which.md`: “Skills teach procedure. MCP grants capability.” Skills = versioned `SKILL.md` workflows in git; MCP = runtime tools/resources outside the repo.
  - [Course 02](../courses/02-rag-knowledge-systems.md): RAG as governed retrieval pipeline (ACLs before ranking, citations, eval) — not only “vector DB in the middle.”
  - [Course 04](../courses/04-mcp-interoperability.md) + [agent governance](../concepts/agent-governance-and-mcp.md): MCP as capability boundary with auth risks (confused deputy, two walls).
- Public POCs compose these rather than picking one: [claims-multiagent-rag](../products/claims-multiagent-rag-poc.md) (RAG), [claims-mcp-oauth](../products/claims-mcp-oauth-poc.md) / [partner-api](../products/claims-partner-api-mcp-poc.md) (MCP), Cursor skills like `xingai-wiki-ingest` (procedure) — [claims family](claims-poc-family-tradeoffs.md).

## Missing (on the poster)

- **Composition:** no diagram of Skill → calls MCP → MCP tool returns RAG hits.
- **Auth / policy** on MCP (OAuth, scopes, Review→Execute).
- **RAG quality:** chunking, ACL, citation faithfulness, eval — only embedding→DB→augment.
- **Skills trust model:** who authors SKILL.md, how it is versioned/reviewed, failure mode “stale instructions” (named in XingAI blog, absent here).
- **Eval / ledger / HITL** for any of the three columns.

## Rethink

- **“vs” is the wrong conjunction.** For XingAI, the useful question is *which layer owns which job*, not *which architecture wins*. Skills without MCP cannot fetch live broker/claims data (blog); MCP without Skills leaves “how we build” unencoded; RAG without either is only document grounding.
- **Skills column conflates two things:** (1) `SKILL.md` playbooks and (2) runtime tool execution (shell/docker). XingAI blog keeps (1) as Skill and pushes live capability to MCP — the poster collapses them under “Agent Skills.”
- **MCP column looks like happy-path connectivity.** Course 04 / oauth POC exist because “choose the right server” without audience-scoped tokens is unsafe.

## Debate (leave open)

| Question | Poster lean | XingAI public lean | Status |
|---|---|---|---|
| Are MCP / RAG / Skills alternatives? | Implied by “vs” | Layers/jobs (blog + courses) | Prefer composition; not a formal ADR |
| Where do agent tools live? | Skills column (shell/git/docker) | Often MCP servers for external systems; Skills for playbooks | Open for IDE-local tools vs remote APIs |
| Is RAG “an architecture” or a retrieval pattern inside agents? | Peer column | Course 02 pattern used *inside* agents/POCs | Open naming; substance: ACLs + eval still required |

## Needs evidence

- Canonical URL / author for this graphic.
- Whether “Drant” is Qdrant (typo) — do not treat as a product claim.
- Any XingAI public doc that endorses exclusive “pick MCP or RAG or Skills” (not found in snapshotted blog post; absence ≠ proof of none elsewhere).

## How to use

- Interview / Course 04–02 probe: “Draw how these three compose; then add auth and ACL.”
- When ingesting marketing diagrams: fail pages that only retell the three columns.

## Sources

`raw/external/2026-07-16-mcp-vs-rag-vs-skills/`; `raw/xingai-tech-blog/posts/2026-06-14-cursor-skills-vs-mcp-when-to-use-which.md`; Course 02/04 entity pages; claims MCP/RAG product pages. Diagram: `verified: partial`.
