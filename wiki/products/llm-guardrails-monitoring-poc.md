# Product: llm-guardrails-monitoring-poc

Chinese: [llm-guardrails-monitoring-poc.zh.md](llm-guardrails-monitoring-poc.zh.md)

**Repo:** [xingai-enterprise-ai-pocs](https://github.com/xingaiapp/xingai-enterprise-ai-pocs/tree/main/pocs/llm-guardrails-monitoring-poc) · **Status:** Runnable · Phase 1 (ADR-010)

Twelve-step **Plan → Build → Validate → Operate** demo with XingAI corrections on each wall. Mock model. Fail-closed skips. Port 8020 UI probes: happy path, injection, risky tool, weak evidence.

## Known

- Pipeline implements steps 1–12 in `backend/pipeline.py` with `passed` / `blocked` / `warned` / `skipped` — public POC README + ADR-010.
- Step 6 scans user + RAG + tool text; step 7 blocks `transfer_funds` via simulated MCP scope wall; step 12 writes ledger `ship_answer` / `escalate_human`.
- Design teaching article and tech blog exist (2026-07-17) and link the POC.

## Missing

- Real OAuth / Entra / APIM (deferred to [claims-mcp-oauth-poc](claims-mcp-oauth-poc.md)).
- Live LLM, vector DB, durable long-running MCP tools.
- Production CI eval suite as a hard gate (only flags logged in-demo).

## Rethink

- Do not read the public poster’s **Tools** rows as this POC’s architecture — the POC’s point is walls, not logos ([synthesis](../syntheses/llm-guardrails-monitoring-vs-xingai.md)).

## Debate

- How much of Validate (steps 8–10) should move into a shared policy service vs stay in-process for teaching POCs?

## Needs evidence

- Classroom / leadership demo outcomes beyond local `pytest` — not measured in-repo yet.

## Connects to

- [llm-guardrails-monitoring-vs-xingai](../syntheses/llm-guardrails-monitoring-vs-xingai.md)
- [claims-mcp-oauth-poc](claims-mcp-oauth-poc.md), [multi-agent-lab](multi-agent-lab.md)
- [Course 03](../courses/03-tool-use-ai-agents.md), [04](../courses/04-mcp-interoperability.md), [06](../courses/06-production-ai-engineering.md)

## Sources

- https://github.com/xingaiapp/xingai-enterprise-ai-pocs/tree/main/pocs/llm-guardrails-monitoring-poc
- https://github.com/xingaiapp/xingai-enterprise-ai-pocs/blob/main/docs/adr/010-llm-guardrails-monitoring-poc.md
- https://github.com/xingaiapp/xingai-tech-blog/blob/main/posts/2026-07-17-llm-guardrails-twelve-steps-not-tool-stickers.md
- https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-07-17-llm-app-guardrails-plan-build-validate-operate.md
