# Synthesis: Claims POC Family — Auth vs Coverage vs Workflow

Four public POCs sit in one repo and look like "more claims demos." They aren't. Read as a deliberate matrix:

| Axis | Narrow tools + real auth | Broad tools + deferred auth | Multi-agent workflow + audit |
|---|---|---|---|
| **Auth-first** | [claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.md) | — | [claims-workflow-v2](../products/claims-workflow-v2-poc.md) uses a *static* service token today; ADR-009 Phase 4 points at oauth POC |
| **Coverage-first** | — | [claims-partner-api-mcp-poc](../products/claims-partner-api-mcp-poc.md) (~18 tools) | workflow-v2's MCP surface is small on purpose (policy/ledger/payments) |
| **Orchestration** | Scripted demo client, not a supervisor | Partner agent assumed external | [multi-agent-lab](../products/multi-agent-lab.md) → [claims-multiagent-rag](../products/claims-multiagent-rag-poc.md) → workflow-v2 (increasing domain fidelity) |

## The tradeoff Course 04 won't say out loud

[Course 04](../courses/04-mcp-interoperability.md) teaches governed capability negotiation. The public POCs split that into two experiments you should not merge in your head:

1. **oauth POC** — prove OAuth 2.1 + PKCE + two walls (scope ≠ settlement policy) on a *tiny* tool surface. Auth is the product.
2. **partner-api POC** — prove OpenAPI→MCP full coverage so a partner isn't blocked waiting for "one more tool." Auth is explicitly deferred (ADR-007).

Combining them is the *next* engineering move, not the starting point. ADR-009 Phase 4 for workflow-v2 is that combination aimed at the workflow's `mcp_server/`.

## Workflow lineage (same domain, different questions)

- **multi-agent-lab** — platform shape (orchestrator, specialists, SQLite traces) with fake tools. Almost no insurance semantics.
- **claims-multiagent-rag** — insurance semantics + RAG citations + human-in-the-loop. Decision *assistant*, not auto-adjudication.
- **claims-workflow-v2** — fixes a specific bad infographic (split fraud, stage-aware resume, ledger). Then deepens into MCP + dual-path LLM + LangGraph. Closest to "Course 05–07 homework that ships tests."

If you only read one POC README, you miss that workflow-v2's production-readiness gap #2 (real OAuth) is already solved *as a sibling POC*, not as missing imagination.

## Event-bus as the odd one out

[event-bus-ai-review](../products/event-bus-ai-review.md) is design-only and event-driven. It answers a different control-plane question: sync supervisor graphs (lab / RAG / workflow-v2) vs decoupled subscribers for AI review + compliance + human approval. Don't force it into the MCP matrix above.

## How to use this page

When asking "which POC should I study for X?":

- MCP auth / confused deputy → oauth POC + Course 04 + third-party MCP article
- MCP tool sprawl / OpenAPI wrapping → partner-api POC + coverage-vs-workflow article
- Multi-agent + RAG + citations → claims-multiagent-rag + Course 02/05
- Decision ledger + production gaps → workflow-v2 + Course 06/07 + [PRODUCTION-READINESS](../products/claims-workflow-v2-poc.md#production-readinessmd--course-06-case-study)

## Sources

Chat synthesis over `raw/pocs/*/README.md`, `raw/pocs/docs/adr/006-*.md`, `007-*.md`, `008-*.md`, `009-*.md`, and Course 04 — not a copy of any single README.
