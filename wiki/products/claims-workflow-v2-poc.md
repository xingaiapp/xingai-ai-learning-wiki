# Product: claims-workflow-v2-poc

**Repo:** [xingai-enterprise-ai-pocs/pocs/claims-workflow-v2-poc](https://github.com/xingaiapp/xingai-enterprise-ai-pocs) · **Status (2026-07-16):** Runnable · Phase 1+2+3 · 40 tests passing

A multi-agent insurance-claims pipeline built to prove three fixes to a popular (but flawed) claims-automation infographic: fraud detection split into pre-assessment Triage and post-assessment Scoring agents, a Case Resolution Router that resumes at a specific stage instead of restarting from intake, and a Decision-Ledger-shaped compliance audit trail every stage writes to. Deepened across three phases into a real MCP data-access boundary (Phase 1), LLM-backed agents with a dependency-light RAG layer (Phase 2), and a LangGraph supervisor (Phase 3).

This is the main public runnable cross-reference in this wiki — nearly every course connects to some piece of it. See each course page's "Connects to" section rather than duplicating the mapping here.

## The three original fixes

1. **Fraud detection split** — `fraud_triage.py` (before Damage Assessment, velocity/tenure signals only) vs. `fraud_scoring.py` (after, cost-anomaly/photo-forensics signals). Each pins a distinct `model_version` for fairness-audit traceability.
2. **Case Resolution Router** — maps `(escalation.reason, escalation.stage, human_decision.outcome)` to a specific re-entry stage; unrecognized combinations fall through to a safe default deny, never a silent restart. Discovered during implementation (not in the original design article): the router had to become *stage-aware*, not just reason-aware.
3. **Compliance & Audit Trail** — every agent decision is an MCP-tool-backed `DecisionLedger` row (see [Concept: Decision Ledger pattern](../concepts/decision-ledger-pattern.md)); adverse-action letters cite the specific policy clause that produced a denial.

## Three-phase deepening (ADR-009)

- **Phase 1 — MCP data boundary:** policy lookup, ledger writes, and payments move behind a hand-rolled JSON-RPC-over-FastAPI `mcp_server/`, in-process by default (via `starlette.testclient.TestClient`, not raw `httpx.ASGITransport` — the latter doesn't support sync calls), or real HTTP when `MCP_SERVER_URL` is set.
- **Phase 2 — LLM agents + RAG:** every LLM-backed agent has a heuristic path (unchanged, default) and an LLM path (dispatched via `llm_client.is_available()`), falling back to heuristic on any `LLMError`. Policy Coverage's LLM path retrieves real clause text (including exclusions) via a ~40-line pure-Python hashing-trick embedding — deliberately no vector database, since the corpus per policy is small and always scoped to one known policy.
- **Phase 3 — LangGraph supervisor:** the same 8 agent functions become graph nodes; the Case Resolution Router's "resume at a specific stage" need is met by compiling a *fresh* graph per call starting at the chosen stage, explicitly **not** real LangGraph checkpointing — a documented, deliberate scope reduction.

## PRODUCTION-READINESS.md — Course 06 case study

Organized by four lenses: AI Agent layer (prompt-injection risk on the free-text `loss_description` field feeding both Fraud agents and Policy Coverage — flagged as unaddressed anywhere in the codebase; uncalibrated heuristic thresholds; no model-risk governance process), MCP layer (no tool schema versioning, no call resilience/circuit-breaker, unbounded ledger retention), automation/ops (no persistence, no observability, no DR plan, no canary rollout), and claims-industry-specific regulatory concerns a generic checklist wouldn't surface (prompt-payment law deadlines, SIU/fraud-bureau reporting, jurisdiction-aware adverse-action letters, PII handling around the LLM call, model change-management).

**Priority order given in that doc:** (1) prompt-injection screening — cheap, closes a real fraud vector; (2) real OAuth in front of `mcp_server` — already fully designed as ADR-009 Phase 4; (3) prompt-payment deadline tracking + LLM data-handling posture; (4) persistence and retention policy together, not persistence alone.

## Connects to

- [Concept: Decision Ledger pattern](../concepts/decision-ledger-pattern.md), [Concept: Cache / fallback LLM discipline](../concepts/cache-first-llm-architecture.md), [Concept: Agent governance and MCP](../concepts/agent-governance-and-mcp.md)
- [Course 05](../courses/05-agent-runtime-multi-agent.md) (LangGraph, state machines), [Course 06](../courses/06-production-ai-engineering.md) (production-readiness gap analysis), [Course 07](../courses/07-enterprise-decision-systems.md) (Decision Ledger), [Course 04](../courses/04-mcp-interoperability.md) (the MCP server itself)
- Sibling public POC: [`claims-mcp-oauth-poc`](https://github.com/xingaiapp/xingai-enterprise-ai-pocs) — real OAuth 2.1 Authorization Server this POC's ADR-009 Phase 4 plans to wire in front of `mcp_server/`; not yet ingested into this wiki.

## Sources

`raw/claims-workflow-v2-poc/README.md`, `PRODUCTION-READINESS.md`, `architecture.md`, `docs/adr/008-claims-workflow-v2-poc.md`, `docs/adr/009-claims-workflow-v2-mcp-multiagent.md`
