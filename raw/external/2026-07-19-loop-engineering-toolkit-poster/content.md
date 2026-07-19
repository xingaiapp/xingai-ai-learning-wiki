# Cobus Greyling — Loop Engineering (README screenshot transcript)

Third-party screenshot, 2026-07-19. Not XingAI-authored. Reference only — do not embed this art on wiki pages.

## Header / claim

- Title: **Loop Engineering**
- Tagline: **Stop prompting. Design the loop. Get a score.**
- Framing: Loop engineering replaces you as the person who prompts the agent — you design the system that does it instead.
- Social proof on page: ~8.2k GitHub stars (as shown on screenshot; not independently verified here).

## Package badges (as shown)

- `loop-audit` v1.6.0
- `loop-init` v1.4.0
- `loop-cost` v1.1.0
- `loop-sync` v1.0.0
- `loop-context` v1.3.0
- `loop-mcp-server` v1.0.0
- `loop-worktree` v1.2.0
- License: MIT
- CI: GitHub Pages (live | interactive), loop-audit dogfood (passing)

## Central diagram (as shown)

Dark background, glowing teal **horizontal infinity (∞)** titled roughly “Loop Engineering: Design the system that prompts your agents.”

Nodes / labels visible on the loop:

- scheduling
- sub-agents (appears more than once)
- worktrees
- persistent state / memory
- skills

## Quick start (as shown)

```text
npx @cobusgreyling/loop-init .
```

Claimed outcome: scaffolds **skills**, **state**, and **budget** files; computes a **Loop Ready** score; prints the first loop command. `--tool` can be `claude`, `codex`, or `opencode`.

## Agent note

This file is a transcript of the screenshot for `raw/` provenance. Critique and XingAI map live in wiki pages — see `SOURCE.md`.
