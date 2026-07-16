# Synthesis: "Layers of AI" vs XingAI curriculum

Popular infographic (user-ingested 2026-07-16): six stacked cylinders — Classical AI → Machine Learning → Neural Networks → Deep Learning → Generative AI → Agentic AI.

Asset: `raw/external/2026-07-16-layers-of-ai/`.

## Known

- On-image labels (visual read, `verified: partial`): Classical (Symbolic / Expert Systems / Knowledge Representation / Logic & Reasoning); ML (Supervised / Unsupervised / Classification / RL / Regression); NN (Perceptrons / Cost / Backprop / Activations / Hidden Layers); DL (Transformers / LSTM / RNN / CNN / Autoencoders); GenAI (LLMs / Diffusion / Multimodal / VAE); Agentic (Memory / Planning / Tool Use / Autonomous Execution). Credit line on image: “Follow Michael - From Pilots to Platforms.”
- XingAI foundation curriculum publicly starts vocabulary at Course 00 and spends most depth on GenAI app boundaries through governed agents (Courses 01–05) plus production/decision/CTO (06–08) — see `raw/courses/README.md` and course entity pages.
- Public claims POCs document deferred auth, production gaps, and two-wall auth as *separate* experiments — not “climb the purple ring and you’re done” ([claims-poc-family-tradeoffs](claims-poc-family-tradeoffs.md)).

## Missing (from the poster)

- Authorization, evaluation, human-in-the-loop, decision ledgers, cost/ops — none appear on the top ring.
- Failure modes (prompt injection, confused deputy, stale checkpoints).
- Any citation or definition of “layer” (historical? dependency? marketing?).

## Rethink

- **Stack ≠ dependency.** Classical rules and ML classifiers still sit inside “agentic” POCs (status machines, heuristic fallbacks). Treating lower rings as obsolete misreads enterprise systems.
- **Height ≠ readiness.** Tool-calling demos without OAuth/policy/ledger remain demos per POC PRODUCTION-READINESS docs.
- **Transformers vs LLMs** split across DL and GenAI rings — overlapping categories, not clean strata.

## Debate (leave open)

- Is “Agentic AI” a **capability layer** (poster) or a **control regime** (Courses 03–04 + MCP POCs)? XingAI materials lean control regime; the poster does not argue the case.
- Should Classical AI be taught as a first-class course band, or only as embedded policy? Curriculum currently embeds it; the poster elevates it as ring 1. No ADR settles “add a Classical course.”

## Needs evidence

- Canonical URL / author page for this exact graphic (not in package).
- Whether any XingAI public course explicitly endorses this six-ring taxonomy (not found in snapshotted course index; absence ≠ disproof — Needs evidence on a full-text search of design repo if required later).

## When to use

Onboarding vocabulary and Course 09 interview probes (“where does governance fit?”). Not as a POC architecture diagram.

## Sources

`raw/external/2026-07-16-layers-of-ai/` (SOURCE.md, notes.md, assets/layers-of-ai.png); `raw/courses/README.md`; claims POC family synthesis. Visual labels: `verified: partial`.
