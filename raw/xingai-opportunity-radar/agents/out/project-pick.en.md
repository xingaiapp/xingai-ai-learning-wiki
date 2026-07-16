# XingAI Project Pick — Decision Card

**Date:** 2026-07-16
**Engine:** manual (Claude, grounded in repo code — see note below)
**Issue:** Agent Adoption's Bottleneck Just Moved From Capability to Certification
**Featured opportunity (from email):** Agent Skill Assurance & Evaluation

> Note on engine: produced by direct inspection of `xingai-agent-firewall`'s
> actual code/ADRs/PRD (not the `_heuristic_pick()` fallback in
> `project_pick.py`, which is hardcoded to the June 28 issue's narrative and
> would mis-match this one). Same output contract as the script; re-run
> `project_pick.py --force-llm` later for a second, independent opinion.

---

## PICK: Agent Skill Assurance & Evaluation → Agent Firewall module

- **Mode:** upgrade (upgrade of `agent-firewall`)
- **Repo home:** `xingai-agent-firewall`
- **Scores:** portfolio 5/5 · founder 5/5 · time-to-signal 4/5 · reuse 5/5

### Why now

`xingai-agent-firewall` already ships policy → risk score → approval → ledger
for live agent tool calls (Claude Code `PreToolUse` hooks, ADR-001/002/003).
What it doesn't have is a *pre-production* certification step: nothing today
imports a Skill/MCP manifest, extracts its requested permissions, runs it
against normal/edge/adversarial test cases, compares it across model
providers, or blocks a regressed version before it ever reaches a live
session. This week's signals (Sonnet 5's cheaper long-task pricing, NVIDIA's
Secure Agent Workspace reference design, Claude Tag's persistent team
context) all point the same direction: more Skills, longer unsupervised
runs, more third-party tool surface — exactly what Firewall's runtime layer
governs, but one lifecycle stage too late. Building this as a Firewall
module reuses the existing Decision ledger schema, dashboard, and policy
engine (`engine/ledger.py`, `engine/policy.py`) instead of forking a second
governance surface — directly satisfies `config/portfolio.yaml`'s
`prefer_upgrade_when: "Bet strengthens audit/trust/governance → agent-firewall"`.

### 2-week MVP

Skill/MCP manifest import → capability + permission extraction → a small
eval dataset (normal/edge/adversarial cases) run in Firewall's existing
sandbox model → risk score + Approve/Restrict/Block written as a Decision
row in the same ledger Firewall's runtime checks already use → a new
"Skills" tab in the existing dashboard next to Queue and Audit.

### Who pays

Same buyer Firewall's phase-2 enterprise path already targets: AI platform
teams, agent builders shipping third-party Skills, security engineers who
already use the approval queue and want a pre-production counterpart to it.

### Business model

Bundle into Firewall's existing Team/Enterprise tier at v1 rather than a
new SKU — fragmenting the ledger across two paid surfaces contradicts the
"prefer upgrade" thesis this pick is built on. Revisit a standalone
Developer $29/month tier only if usage data shows non-Firewall users want
just the eval piece in isolation.

## Rejected (do not start these instead)

- **Research Experiment OS** (new repo): Real, high-scoring opportunity (96) and correctly a *new* vertical — no existing repo owns a controlled-experiment ledger for research agents. Not rejected on merit; sequenced behind this pick because starting two new/upgraded repos the same week splits founder attention, and this pick reuses infra that ships faster. The sandbox + eval-run primitive built for Skill Assurance should be reused here rather than rebuilt.
- **SAT Teacher & Tutor Platform** (upgrade of `sat`): Genuine opportunity — Claude for Teachers validates a second buyer (teachers) for SAT AI's existing tutor product. Not a governance bet, needs its own multi-week lesson/rubric content pipeline rather than an eval harness — sequence after the two infra bets above.
- **Decision Memory Engine** (new repo vs. shared schema patch): Already partially implemented as the shared Decision ledger schema every XingAI product — including Firewall — already reuses. The two fields Memora-style memory would add (`actual_outcome`, `lesson`) belong as a schema patch to the existing shared ledger, not a standalone new product, and can ride along with this week's Firewall ledger work.
- **Standalone new repo for Skill Assurance (no XingAI chrome):** Orphan domain fights portfolio reuse (ledger schema, dashboard, i18n/theme). Violates the "prefer upgrade of an existing *.xingai.app over orphan new domains" principle in `config/portfolio.yaml`.

## Do not build

- Generic chatbot wrappers with no decision output
- New product that recomputes Invest decisions in the request path
- A parallel Decision ledger schema instead of reusing Firewall's existing one
- A standalone "Agent Skill Assurance" SaaS with no relationship to Firewall's runtime enforcement — fragments the governance story into two unconnected ledgers

## Handoff

- Next: confirm this pick, then open a scaffolding PR in `xingai-agent-firewall` adding a `skills/` module that reuses `engine/ledger.py` and `engine/policy.py`; see the Content Pack for the detailed architecture recommendation and Cursor prompt.
- Radar theme: Agent Adoption's Bottleneck Just Moved From Capability to Certification

_Not investment advice. Editorial decision aid for XingAI founders only._
