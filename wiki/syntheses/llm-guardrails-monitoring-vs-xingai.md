# Synthesis: LLM Guardrails & Monitoring Ladder vs XingAI

Chinese: [llm-guardrails-monitoring-vs-xingai.zh.md](llm-guardrails-monitoring-vs-xingai.zh.md)

Two user-attached teaching diagrams share the title **How to Build LLM Apps with Guardrails and Monitoring**:

| Variant | Shape | Raw file |
|---|---|---|
| A | 10-step zigzag (Alok Sharan credit) | `raw/.../alok-sharan-reference.png` |
| B | 12-step **Plan / Build / Validate / Operate** grid | `raw/.../12-step-plan-build-validate-operate-reference.png` |

Both are checklists with **Tools** rows. Neither is an enterprise control plane. Wiki embeds the **XingAI-corrected** map only (evaluate → fix → correct → draw):

![XingAI map — corrected Decide / Gate / Run path](../assets/ux/llm-app-guardrails-monitoring/xingai-map.png)

## Known

- **A and B** both push: use case, RAG, prompts, input/output checks, tool limits, monitor, eval, secure deploy (`raw/external/2026-07-17-llm-guardrails-monitoring-poster/`).
- **B improves on A:** step 2 **Map Risks & Policy** before model choice; step 12 **Iterate & Govern**; explicit Checks (grounding, block release); no “GPT-5.5” sticker visible; footer phases clearer than A’s snake.
- Directionally aligns with Course 03 validate-before-act and [agent-governance-and-mcp](../concepts/agent-governance-and-mcp.md) (policy ≠ scope alone).
- XingAI map footer: agent may be probabilistic; auth, tools, workflow state must stay deterministic ([ai-architecture-digest-2026-07-17](ai-architecture-digest-2026-07-17.md)).

## Missing (still on B — present on XingAI map)

- **MCP two-wall** — Resource Server + scope + independent business policy ([Course 04](../courses/04-mcp-interoperability.md)).
- **Untrusted observations** beyond user text — RAG, tool returns, other agents.
- **Evidence RAG** with sufficiency stop — not index/chunk/tools logos ([Course 02](../courses/02-rag-knowledge-systems.md)).
- **Agent Run traces + Decision Ledger** — not only latency/cost dashboards ([Course 06](../courses/06-production-ai-engineering.md)).
- **Identity continuous controls** — Entra / APIM ([Course 10](../courses/10-oauth-oidc-azure-identity.md)), not only a late “Deploy Securely” card.
- **Durable approval** for side effects — timeout/compensation.

## Rethink

- **B is a better ladder than A, not a fixed architecture.** Tools columns still teach sticker-driven design.
- **A’s GPT-5.5** — unverified; never repeat on XingAI surfaces.
- **Input guards on B** still center injection/PII — under-weights Agent Traps on retrieved/tool text.
- **Deploy Securely (11) + Iterate (12)** help Operate, but auth posture must start in Plan/Decide — not appear first at ship time.
- Card **colors on B ≠ footer phases** — visual debt; XingAI map uses Decide / Gate / Run bands instead.

## Debate

- Guardrail products inside the agent loop vs policy service in front of MCP tools?
- Is Plan/Build/Validate/Operate enough, or must Gate (walls) be an explicit band before Operate?

## Needs evidence

- No canonical URL for A or B.
- Whether B is a community rewrite of A or an independent diagram — **unknown** (no credit on B image).
- XingAI public POC end-to-end Gate→Run in production — **unknown** from this ingest alone.

## Connects to

- [agent-governance-and-mcp](../concepts/agent-governance-and-mcp.md)
- [Course 02](../courses/02-rag-knowledge-systems.md), [03](../courses/03-tool-use-ai-agents.md), [04](../courses/04-mcp-interoperability.md), [05](../courses/05-agent-runtime-multi-agent.md), [06](../courses/06-production-ai-engineering.md), [10](../courses/10-oauth-oidc-azure-identity.md)
- [ai-architecture-digest-2026-07-17](ai-architecture-digest-2026-07-17.md)

## Sources

- Raw: `raw/external/2026-07-17-llm-guardrails-monitoring-poster/` (A + B references + `notes.md`)
- UX (wiki embed only): `wiki/assets/ux/llm-app-guardrails-monitoring/xingai-map.png`
