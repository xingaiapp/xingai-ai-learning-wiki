# Synthesis: Enterprise agent architecture poster vs XingAI public map

Reference-architecture infographic (user-ingested 2026-07-16, credit on image: Rishi): Inputs → Plan/Reason/Act/Respond orchestrator + tools → Context/Memory → Response guardrails → LLMOps → Platform foundation.

Asset: `raw/external/2026-07-16-enterprise-ai-agent-architecture/`.

This page is **not** a redraw of the boxes. It asks what the poster claims, what XingAI public courses/POCs already cover, and where both sides leave holes.

## Known

- Poster labels (visual read, `verified: partial`): six regions listed in `notes.md` — Inputs; Orchestration loop PLAN→REASON→ACT→RESPOND with tool icons including Knowledge Base and Payment Gateways; Memory (working / vector RAG / optional KG / episodic); Response guardrails including Hallucination Check and Confidence Scoring; LLMOps (observe, LLM-as-judge eval, diagnostics, gating, release); Platform foundation (security, privacy, audit, FinOps, multi-tenant, etc.).
- XingAI public curriculum already teaches pieces of this map under different names:
  - Loop / runtime → [Course 05](../courses/05-agent-runtime-multi-agent.md), [loop engineering](../concepts/loop-engineering.md)
  - RAG → [Course 02](../courses/02-rag-knowledge-systems.md)
  - Tools + approval → [Course 03](../courses/03-tool-use-ai-agents.md)
  - Production eval/gates → [Course 06](../courses/06-production-ai-engineering.md)
  - Audit / decision records → [Course 07](../courses/07-enterprise-decision-systems.md), [decision ledger](../concepts/decision-ledger-pattern.md)
  - Auth walls for tools → [agent governance / MCP](../concepts/agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.md)
- Public POCs implement **slices**, not the full poster: e.g. [claims-workflow-v2](../products/claims-workflow-v2-poc.md) has orchestration + dual-path LLM + ledger-shaped writes + PRODUCTION-READINESS gaps; [claims-multiagent-rag](../products/claims-multiagent-rag-poc.md) has supervisor+RAG+HITL; oauth POC has real auth on a thin tool surface ([family](claims-poc-family-tradeoffs.md)).

## Missing (on the poster)

- **Authorization as two walls** (OAuth scope vs business policy) — “Security & Access Control” is a foundation tile; no Review→Execute / settlement-cap pattern.
- **MCP / tool schemas / confused-deputy** — tools are icons (CRM, payments) without capability negotiation.
- **Decision Ledger / adverse-action audit** as a first-class data product — “Audit Logs” is listed, not an immutable decision record with `model_version`.
- **Human-in-the-loop placement** — no explicit Approve node; only post-response guardrails.
- **Stop conditions / anti-loop** — iterative loop drawn; no “when to halt / escalate.”
- **Prompt-injection on tool inputs** — Course 03 / workflow-v2 PRODUCTION-READINESS care about this; poster does not name it.

## Missing (in XingAI public POCs relative to the poster)

Per snapshotted POC docs (not a claim that private products lack these):

- Full LLMOps loop (LLM-as-judge, canary, prompt/RAG config versioning) — Course 06 teaches; claims POCs mostly list gaps in PRODUCTION-READINESS rather than shipping the loop.
- Knowledge Graph band — optional on poster; not a focus of snapshotted claims POCs.
- Platform multi-tenant / FinOps as running code — foundation tiles; treat as **Needs evidence** for any specific XingAI public POC.

## Rethink

- **Poster completeness ≠ implemented architecture.** Drawing Hallucination Check + FinOps does not mean they exist; XingAI’s own POC readiness docs are the better honesty model.
- **Guardrails after RESPOND under-protect ACT.** If ACT can hit Payment Gateways, policy must gate *tool calls* (Course 03 Approve / oauth Review→Adjudicate), not only the final chat string.
- **“Knowledge Base” as a tool vs RAG memory** — conflating retrieval with tool use hides ACL-before-rank (Course 02).
- **LLM-as-a-Judge as primary eval** — Course 06 and engineering patterns also push golden/adversarial sets and deterministic gates; judge-only eval is contested (see Debate).

## Debate (leave open)

| Fork | Poster lean | XingAI public lean | Status |
|---|---|---|---|
| Auth | Platform tile | Dedicated MCP OAuth POC + deferred auth on coverage POC | Unsettled as one combined system in public POCs |
| Eval | LLM-as-Judge highlighted | Course 06: metrics + gates; judge optional | Open |
| Memory | Working + vector + optional KG + episodic | POCs: session/state + light RAG; KG rare | Open whether KG is required for “enterprise” |
| Control plane | Sync orchestrator | Also event-bus design-only POC | Open ([event-bus](../products/event-bus-ai-review.md)) |

## Needs evidence

- Canonical URL / longer writeup by Rishi for this diagram.
- Whether any XingAI **public** POC implements a named hallucination check or confidence score in code (not asserted here).
- Exact placement of human approval in any system that matches this poster (pre-ACT vs post-RESPOND).

## How to use in this wiki

- Checklist when reading Course 05–06 or a new agent POC: which poster boxes are **Known in code**, which are **Missing**, which are **marketing tiles**.
- Pair with [Layers of AI vs curriculum](layers-of-ai-vs-curriculum.md): that poster is taxonomy; this one is control-plane — neither replaces PRODUCTION-READINESS.

## Sources

`raw/external/2026-07-16-enterprise-ai-agent-architecture/` (SOURCE.md, notes.md, assets/); course/POC pages cited above; `raw/pocs/claims-workflow-v2-poc/PRODUCTION-READINESS.md` for gap-honesty precedent. Diagram labels: `verified: partial`.
