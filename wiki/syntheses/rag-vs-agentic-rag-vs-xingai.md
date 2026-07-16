# Synthesis: RAG vs Agentic RAG (poster) vs XingAI map

Chinese: [rag-vs-agentic-rag-vs-xingai.zh.md](rag-vs-agentic-rag-vs-xingai.zh.md)

Three-panel architecture poster (user-ingested 2026-07-16, **no legible author credit**): **RAG** (linear embed→vector DB→augment→LLM) · **AI Agent** (memory/planning/tools over data sources) · **Multi-Agent RAG** (aggregator + specialists via **MCP Servers** to local / search / cloud).

Asset: `raw/external/2026-07-16-rag-vs-agentic-rag/`.

Related marketing cut (peer columns, not ladder): [MCP vs RAG vs Skills](mcp-vs-rag-vs-skills.md).

## Known

- Panel structure (visual, `verified: partial`): see `notes.md`. Title says “vs”; body shows three architectures. Multi-Agent panel names MCP Servers, ReAct, CoT, short/long memory; vendor logos (Kagi, AWS, Azure) appear as example backends.
- XingAI public teaching already covers the *jobs* these panels sketch:
  - Governed RAG pipeline (ACL before rank, citations, eval) → [Course 02](../courses/02-rag-knowledge-systems.md)
  - Tool use / planning / approval → [Course 03](../courses/03-tool-use-ai-agents.md)
  - MCP as capability boundary → [Course 04](../courses/04-mcp-interoperability.md), [agent governance](../concepts/agent-governance-and-mcp.md)
  - Multi-agent runtime / when to add agents → [Course 05](../courses/05-agent-runtime-multi-agent.md)
- Public POCs compose rather than pick a panel: [claims-multiagent-rag-poc](../products/claims-multiagent-rag-poc.md) (supervisor + specialists + RAG + HITL), [claims-workflow-v2](../products/claims-workflow-v2-poc.md) (orchestration + dual-path LLM + light RAG, often **without** a vector DB for a small policy corpus), [claims-mcp-oauth](../products/claims-mcp-oauth-poc.md) / [partner-api](../products/claims-partner-api-mcp-poc.md) (MCP surfaces) — [family](claims-poc-family-tradeoffs.md).

## Missing (on the poster)

- **RAG quality / safety (Course 02):** document ACLs before ranking, citation faithfulness eval, poisoned/stale indexes, “citation-shaped” unsupported claims — Standard RAG panel is happy-path only.
- **Auth / two-wall policy on MCP** — Multi-Agent panel draws MCP Servers to local/search/cloud with no OAuth, scopes, Review→Execute, or settlement caps ([oauth POC](../products/claims-mcp-oauth-poc.md)).
- **Human-in-the-loop / Decision Ledger / PRODUCTION-READINESS** — none of the three panels.
- **Stop conditions / cost / cache-first dual-path** — agent panels show loops implicitly; no halt/escalate or [cache-first](../concepts/cache-first-llm-architecture.md).
- **When not to use a vector DB** — Course 02 / workflow-v2 Phase 2 guidance for small stable corpora is invisible; Standard RAG assumes Vector Db.

## Rethink

- **“vs” is the wrong conjunction again.** XingAI POCs stack retrieval *inside* agents and MCP *beside* RAG. The useful question is which panel’s *job* you need in one system, not which box you “are.”
- **Middle panel is “AI Agent,” not “Agentic RAG.”** Tools↔Data Sources without an explicit retrieve→ground→cite path can be plain tool-calling. Calling that Agentic RAG without grounding/citation discipline blurs Course 02 vs Course 03.
- **Multi-Agent RAG ≈ Course 05 aggregator story + Course 04 pipes** — closest rhyme to [claims-multiagent-rag](../products/claims-multiagent-rag-poc.md) and workflow-v2’s supervisor — but the poster sells autonomy; public POC docs sell escalation and deferred auth.
- **MCP as the only data plane for all specialists** matches XingAI’s “capability boundary” teaching more than the MCP|RAG|Skills peer-column poster — still unsafe without walls.

## Debate (leave open)

| Fork | Poster lean | XingAI public lean | Status |
|---|---|---|---|
| Are standard RAG / agent / multi-agent RAG alternatives? | Title “vs” | Composition inside one product | Prefer composition |
| Must RAG mean a Vector Db? | Standard panel yes | Course 02 / workflow-v2: not always | Open naming; corpus size decides |
| Is “Agentic RAG” a real category or marketing? | Middle + bottom panels | Split: retrieval discipline (02) vs agent control (03–05) | Open vocabulary |
| Where do MCP servers sit? | Only Multi-Agent panel | Course 04 + claims MCP POCs for single-agent tools too | Open diagram convention |

## Needs evidence

- Canonical URL / author for this graphic.
- Whether any XingAI **public** course uses the phrase “Agentic RAG” as an official term (not asserted from snapshot index alone).
- Whether the faint corner mark (if any) identifies a publisher — treat as unknown until readable.

## How to use

- Course 02–05 interview probe: “Redraw without ‘vs’; mark ACL, citation eval, and MCP auth on the Multi-Agent panel.”
- Pair with [mcp-vs-rag-vs-skills](mcp-vs-rag-vs-skills.md): that poster treats RAG as a peer architecture; this one treats RAG as a maturity ladder into agents.
- Do **not** treat vendor logos (Kagi/AWS/Azure) as XingAI product choices.

## Sources

`raw/external/2026-07-16-rag-vs-agentic-rag/` (SOURCE.md, notes.md, assets/); Courses 02–05; claims POC family; [mcp-vs-rag-vs-skills](mcp-vs-rag-vs-skills.md). Diagram: `verified: partial`.
