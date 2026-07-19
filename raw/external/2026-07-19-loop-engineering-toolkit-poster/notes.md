# Notes — evaluate → fix → correct → draw

## Classification

- Third-party **Cobus Greyling “Loop Engineering”** toolkit README screenshot (stars, package badges, infinity diagram, `npx @cobusgreyling/loop-init`).
- Ownership: **reference-only**.
- Distinct from XingAI public pattern `loop-engineering-three-layer` (Context / Harness / Loop).

## Source evaluation (vs XingAI)

- **Source claim (1 line):** Stop prompting — scaffold a loop (skills + state + budget), get a “Loop Ready” score, run forever via scheduling / sub-agents / worktrees / skills / memory.
- **Right (keep):**
  - Prefer designed loops over one-shot chat prompts (aligns with XingAI “beyond prompt engineering”).
  - Persistent state / memory matters.
  - Budget as a first-class concern (toolkit has `loop-cost`; XingAI wants token/budget stop).
  - Skills as reusable procedures (XingAI harness layer) — when not conflated with MCP tools.
- **Wrong (must fix):**
  - Error: Glowy **infinity** implies endless run → Correction: every production loop needs **hard stop** (max iterations, budget, no-progress, timeout, HITL).
  - Error: Diagram is a **capability shopping list** (scheduling, worktrees, sub-agents, skills) without layer separation → Correction: XingAI **three layers** — Context | Harness | Loop.
  - Error: “Get a score” / Loop Ready as architecture → Correction: readiness score ≠ stop conditions, ledger, or auth walls.
  - Error: `loop-mcp-server` badge implies MCP = packaged → Correction: MCP is a **governed capability boundary** (two walls), not a module sticker.
  - Error: Same “sub-agents” twice on infinity without Course 05 rule → Correction: add peers only for specialization / trust separation / parallelism; no cyclic delegation.
- **Missing (add if needed):**
  - Entry point → loop body (Plan → Execute → Evaluate) → **explicit stop**.
  - Human approval before high-risk ACT (trade / deploy / send).
  - Decision ledger / eval after the run.
  - Separation of Context vs Harness vs Loop (pattern doc).
- **Dangerous if followed as-is:**
  - Shipping “design the system that prompts your agents” as infinite automation without stop / HITL.
  - Treating worktrees + scheduling as substitutes for policy walls on tools.
  - Confusing XingAI “Loop Engineering” teaching with this npm toolkit brand.

## XingAI understanding map (post-fix)

- **Keep:** loops beat prompts; state; budget; skills as procedures.
- **Fixed claims (on PNG):** three stacked layers; Loop band shows Entry → body → Stop table; Harness shows MCP walls + skills ≠ tools; STOP / HITL badges.
- **Drop:** infinity glow art; GitHub star count; package version badge row; `npx @cobusgreyling/...`; claude/codex/opencode tool shopping; dark neon aesthetic.
- **Add:** Context / Harness / Loop labels from `loop-engineering-three-layer`; Course 05 / 04 footer; “not a Loop Ready scorecard.”
- **Regroup:** horizontal **stacked bands** (not ∞).
- **One-glance claim:** *XingAI Loop Engineering = Context + Harness + Loop with hard stops — not an infinite agent kit.*
