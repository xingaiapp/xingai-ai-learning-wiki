# Notes

## User vs Agent

- **User (earlier):** `/xingai-ux-png` with Alok 10-step poster → XingAI map drawn.
- **User (2026-07-17 evening):** `/xingai-wiki-ingest` with 12-step Plan/Build/Validate/Operate diagram (same title family).
- **Agent:** Snapshot both as raw reference only; update synthesis critique; keep embedding XingAI-corrected map (not either poster).

## Source evaluation — variant A (10-step Alok)

- **Source claim:** Ten-step ladder with per-step tool logos (use case → deploy).
- **Wrong highlights:** GPT-5.5 sticker; tools = architecture; one-shot RAG; jailbreak-only input; deploy-last = security done; metrics-only monitor.
- Full Error→Correction list: see prior section below (still valid).

## Source evaluation — variant B (12-step Plan/Build/Validate/Operate)

- **Source claim (1 line):** Twelve steps under Plan → Build → Validate → Operate, with per-card Tools rows and Checks.
- **Right (better than A):**
  - **Step 2 Map Risks & Policy** before model choice — risk/policy matrix early (aligns with XingAI Decide/auth posture).
  - **Step 12 Iterate & Govern** — closes the loop (failures → fixes, risk reviews).
  - Explicit **Checks** on many cards (grounding, block release on eval failure, canary).
  - Footer phases Plan/Build/Validate/Operate are clearer than a zigzag snake.
  - No “GPT-5.5” visible on this variant.
- **Wrong (must still fix for XingAI):**
  - Error: **Tools columns still = architecture** (LangChain/Pinecone/CrewAI/K8s stickers) → Correction: MCP Resource Server + two-wall + durable approval; tools fill slots.
  - Error: **RAG still pipeline/index-centric** (ingest/chunk/vector) without evidence sufficiency stop → Correction: evidence loop + stop/escalate (Course 02).
  - Error: **Input guardrails still user-injection/PII-centric** → Correction: all untrusted observations (RAG, tool returns, other agents).
  - Error: **Tool & API controls = agent SDK logos** → Correction: scope wall + policy wall; not CrewAI/LangGraph as the control plane.
  - Error: **Monitor = latency/cost/refusal dashboards** → Correction: Agent Run traces (goal→tool→outcome) + Decision Ledger.
  - Error: **Deploy securely still a late Ship box** → Correction: identity/APIM designed from Plan risk; continuous not checkbox.
  - Error: Card **colors ≠ footer phases** (visual mismatch) — teaching UX debt; XingAI map uses Decide/Gate/Run bands instead.
- **Missing vs XingAI map:** MCP two-wall naming; durable workflow for long tools; architecture router; Course 10 identity spine as first-class.
- **Dangerous if followed as-is:** Better process than A, still ships a tool-shopping control plane.

## Source evaluation — variant A detail (10-step)

- **Right (keep):** use case/risk; model by needs; prompt+refusal; I/O checks; human approval; monitor+eval.
- **Wrong (must fix):**
  - Error: GPT-5.5 sticker → Correction: model-by-task-class; no unverified versions.
  - Error: Tools = architecture → Correction: walls first.
  - Error: One-shot RAG → Correction: evidence loop.
  - Error: Jailbreak-only input → Correction: all untrusted observations.
  - Error: Tool control = SDK logos → Correction: MCP two-wall + durable approval.
  - Error: Deploy-last = security done → Correction: auth from Decide; continuous identity.
  - Error: Monitor = latency/cost only → Correction: Agent Run traces + eval gates.

## XingAI understanding map (post-fix) — unchanged teaching target

- Decide / Gate (walls) / Run with corrected claims on `wiki/assets/ux/llm-app-guardrails-monitoring/xingai-map.png`.
- Variant B’s early policy + iterate/govern reinforce Decide and Run; they do **not** replace MCP walls or evidence stop on the XingAI map.
