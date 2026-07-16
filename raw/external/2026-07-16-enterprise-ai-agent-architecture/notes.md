# Visual notes — Enterprise AI Agent Architecture (Rishi)

## Title / credit

- Title: “Enterprise AI Agent Architecture: From Orchestration to Operations for Reliable, Scalable & Governed AI”
- Author line on image: Rishi
- Legend: Input / Orchestration / Context-Memory / Output / Feedback / Tools flows (color-coded arrows)

## Boxes observed (verified: partial)

1. **Inputs** — User Prompt, Chat History, System Prompt, User/System Context, Files/Documents, APIs/Systems → into orchestration.
2. **Agent Orchestration Engine** — Iterative loop: PLAN → REASON → ACT → RESPOND; Tools & Integrations (Calendar, CRM/ERP, Knowledge Base, Email/Slack, Payment Gateways, Custom APIs).
3. **Context & Memory** — Working Memory; Vector Store (RAG); Knowledge Graph (optional); Long-term / Episodic Memory.
4. **Response & Guardrails** — Safety & Policy, Content Moderation, PII, Hallucination Check, Confidence Scoring → Final Response.
5. **LLMOPS** — Observability & Tracing; Evaluation (LLM-as-a-Judge); Diagnostics; Gating; Release & Deploy (prompt/model/RAG/tool versioning); Observe→Improve→Release.
6. **Platform Foundation** — Security & Access; Privacy & Governance; Audit Logs; Model Management; Cost/FinOps; Monitoring; Multi-tenant; Scalability & Resilience.

## Ambiguities

- Guardrails drawn *after* RESPOND path — unclear if ACT (payments, CRM writes) is blocked pre-tool or only post-text.
- “Knowledge Base” under Tools vs Vector Store under Memory — same store or different?
- Feedback dashed arrows into orchestration — no stated stop conditions or human gate.
- No MCP / OAuth / Decision Ledger vocabulary on the poster.
