# Product: xingai-opportunity-radar

**Type:** editorial/agent pipeline (writing pipeline for weekly issues), not the consumer-facing Radar product — that's `xingai-founder`, per that repo's own ADR-001.

A three-stage agent pipeline that turns raw external signal (an AI-lab blog post, a pasted report) into a build decision: **issue** (normalized `TEMPLATE.md` 8-section write-up: Executive Summary, Top Opportunity, Why It Matters, Build This Week, Investment Angle, XingAI Application, One Sentence Insight, Sources) → **Decision Card** (`project_pick.py`: which XingAI repo to build/upgrade, with rejected alternatives on record) → **Content Pack** (`content_pack.py`: deep analysis, architecture recommendation, Cursor prompt, PRD draft, full references).

## This session's run through the pipeline (2026-07-16)

Input: a pasted Chinese-language radar report ranking **Agent Skill Assurance & Evaluation** as the top Build-Now opportunity (score 98). Two of the report's cited signals ("Microsoft Memora", Google "Personal Health Agent") never resolved to a verifiable primary source in a web-search pass and are flagged `NEEDS MANUAL REVIEW` in the issue file rather than cited as fact — the pipeline's own `chatgpt_intake.py` convention explicitly forbids fabricating a source URL, and this run honored that even though it was done by hand rather than through that script.

**Decision Card outcome:** upgrade [xingai-agent-firewall](xingai-agent-firewall.md) with a new `skills/` module, rather than a new repo — reasoning grounded in `portfolio.yaml`'s `prefer_upgrade_when: "Bet strengthens audit/trust/governance → agent-firewall"` rule, and in the fact that Firewall already has the runtime half of exactly this governance story (see [Concept: Agent governance and MCP](../concepts/agent-governance-and-mcp.md)). Three alternatives explicitly rejected with reasons, not silently dropped: Research Experiment OS (real opportunity, correctly a *new* repo, sequenced later for attention-splitting reasons not merit), SAT Teacher & Tutor Platform (real, but a content pipeline not a governance bet), Decision Memory Engine (already partially implemented as the shared Decision Ledger schema — should be a schema patch, not a new product).

## portfolio.yaml — the guardrails behind every pick

`prefer_upgrade_when` rules (governance bets → agent-firewall; research→product bets → research/founder; team Slack agent ops → new vertical *only if* Firewall can't absorb it) and `do_not_build` (generic chatbot wrappers with no decision output; a new product recomputing Invest decisions in the request path; a second Decision Ledger schema instead of reusing an existing one). This is the same file `xingai-learn`'s ADR-001 now cites (after this session's fix) as the portfolio-wide version of its own product-boundary discipline.

## Connects to

- [xingai-agent-firewall](xingai-agent-firewall.md) — the target of this session's pick.
- [Course 08](../courses/08-ai-leadership-cto.md) — this pipeline's Decision Card is a real, working instance of that course's portfolio-scoring discipline (score, but reason explicitly, don't let the number alone decide).
- [Concept: Agent governance and MCP](../concepts/agent-governance-and-mcp.md) — the runtime-vs-pre-production gap this pick was chosen to close.

## Sources

`raw/xingai-opportunity-radar/issues/2026-07-16-agent-skill-assurance-and-evaluation.md`, `agents/out/project-pick.en.md`, `agents/out/content-pack.en.md`, `portfolio.yaml`
