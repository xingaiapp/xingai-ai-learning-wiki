# Synthesis: Cobus “Loop Engineering” toolkit vs XingAI three-layer loop

Chinese: [loop-engineering-toolkit-vs-xingai.zh.md](loop-engineering-toolkit-vs-xingai.zh.md)

Screenshot of **Cobus Greyling Loop Engineering** README (stars, package badges, glowing infinity diagram, `npx @cobusgreyling/loop-init`, “Loop Ready” score). Third-party art stays **reference-only** under `raw/`. Wiki embeds the **XingAI-corrected** map only:

![XingAI map — Context / Harness / Loop with hard stops; not an infinite agent kit](../assets/ux/loop-engineering-vs-xingai/xingai-map.png)

Asset: `raw/external/2026-07-19-loop-engineering-toolkit-poster/` (`verified: partial`).

## Known

- **Poster (visual):** tagline “Stop prompting. Design the loop. Get a score.”; infinity nodes for scheduling / sub-agents / worktrees / skills / persistent memory; scaffolds skills + state + budget; `--tool` claude|codex|opencode. Cite `assets/cobusgreyling-loop-engineering-reference.png` + `notes.md`.
- **Shared intent (directional):** prefer engineered loops over open-ended chat — same slogan family as XingAI “beyond prompt engineering.” Cite [Concept: Loop engineering](../concepts/loop-engineering.md).
- **XingAI pattern (public):** separate **Context | Harness | Loop**; Loop requires entry, body, **programmatic stop**; guardrails include max iterations, token budget, no-progress, timeout, human approval. Cite `raw/xingai-engineering-system/patterns/loop-engineering-three-layer.md`.
- **Harness ≠ prompt:** tools/MCP need walls ([agent governance](../concepts/agent-governance-and-mcp.md)); multi-agent needs Course 05 specialization rule ([Course 05](../courses/05-agent-runtime-multi-agent.md)).

## Missing (on the poster — on XingAI map)

- Layer separation (Context / Harness / Loop).
- Hard **STOP** panel (iterations, budget, no-progress, timeout, HITL before high-risk ACT).
- MCP **two walls** (scope + business policy).
- Skills vs live tools distinction.
- Decision ledger / post-run eval (still thin on map — open).
- Star counts / package versions as architecture (intentionally dropped).

## Rethink

- **Infinity art teaches the wrong stop story.** XingAI’s test: remove stop conditions and the agent runs forever → loop layer is missing. Glow ∞ fails that test visually.
- **“Loop Ready” score ≠ production loop.** Scaffolding readiness is useful for a toolkit; it is not Auth, Ledger, or Stop.
- **Same English phrase, different object.** XingAI “Loop Engineering” is a **control-loop architecture**. The poster is an **OSS agent scaffolding brand**. Do not merge them in interviews or ADRs without a cite.
- **Worktrees / scheduling are harness options**, not the definition of a loop.

## Debate (leave open)

| Question | Poster lean | XingAI public lean | Status |
|---|---|---|---|
| Is a readiness score enough gate? | Central (“get a score”) | Score optional; stop + HITL required | Prefer hard stops |
| Are worktrees part of “the loop”? | On the ∞ diagram | Harness/runtime detail | Open naming |
| Should XingAI adopt this npm kit? | Implied by screenshot | Unknown — not evaluated as a dependency here | Needs evidence |

## Needs evidence

- Canonical GitHub URL for this README (screenshot only).
- Whether `@cobusgreyling/loop-*` packages implement programmatic stop conditions matching the XingAI table (not verified from image alone).
- Any XingAI public ADR that endorses this toolkit by name (not found in wiki at ingest).

## How to use

- When someone pastes this README: ask them to redraw **three layers + STOP** before talking modules.
- Point to [loop-engineering](../concepts/loop-engineering.md) for XingAI meaning; keep this synthesis as the brand disambiguation.

## Sources

`raw/external/2026-07-19-loop-engineering-toolkit-poster/`; `raw/xingai-engineering-system/patterns/loop-engineering-three-layer.md`; concept + Courses 03–05. `verified: partial`.
