# XingAI Agent Firewall

**Every agent tool call passes through: policy check → risk score → approval → ledger.**

AI coding agents are strong enough to be dangerous. Mozilla's 0din team showed a clean-looking GitHub repo can trick Claude Code into running malicious commands — the agent's helpfulness *is* the attack surface. The fix is architectural, not model-level: a policy layer between the agent and the world.

## What It Does

```
Agent tool call (Bash / file write / network / secrets)
  ↓ adapter:  harness hook intercepts the call (Claude Code PreToolUse at v1)
  ↓ policy:   YAML rules → allow | deny | review
  ↓ risk:     deterministic score 0–100 from weighted signals
  ↓ approval: high-risk calls pause for human approval (queue UI)
  ↓ ledger:   every verdict written as a Decision row (shared XingAI schema)
  ↓ dashboard: audit trail, risk trends, policy hit stats
```

The agent never talks to the shell directly on gated categories; the firewall's verdict is enforced by the harness hook (non-zero exit = blocked).

## Demo Scenario

Reproduce the 0din-class attack safely: a repo whose README/build files instruct the agent to `curl | sh` from an unknown host. With the firewall on, the call is intercepted, scored high (untrusted-origin instruction + network + shell pipe), routed to the approval queue, and logged — the user sees *what* the agent tried to run and *why* it was flagged, before anything executes. The untrusted-origin signal is real: `SessionStart`/`PostToolUse`/`UserPromptSubmit` hooks track whether the agent read untrusted content this turn (ADR-004) — reading the malicious README is what pushes the score from `review` into `deny`.

## Stack

- **Policy engine + API:** Python 3.12, FastAPI, SQLite (WAL) — synchronous verdicts, local-first
- **Adapter:** Claude Code hooks (`PreToolUse`, `PostToolUse`, `SessionStart`, `UserPromptSubmit`) at v1; MCP gateway proxy is the phase-2 enterprise path
- **Dashboard:** Next.js 16, TypeScript, Tailwind, Shadcn UI — reads ledger, renders queue + audit views
- **Deploy:** local-first at v1 (the firewall must work offline); Vercel + Fly.io for the team dashboard later

## How It Differs from Sibling Products

| Product | Records decisions about | Human in the loop |
|---------|------------------------|-------------------|
| Invest Decision Engine | market recommendations | human executes trades |
| Research-to-Startup Agent | startup plans | human decides to build |
| **This repo** | **agent tool calls** | **human approves risky execution** |

Same XingAI thesis — AI recommends, human decides, everything is auditable — applied to the agent's own actions instead of the user's portfolio or roadmap.

## ADRs

- [ADR-001: Interception point — harness hooks first, MCP gateway later](docs/adr/001-interception-point.md)
- [ADR-002: Risk scoring — deterministic rules first, LLM advisory only](docs/adr/002-risk-scoring-model.md)
- [ADR-003: Approval workflow + Decision Ledger reuse](docs/adr/003-approval-workflow-ledger.md)
- [ADR-004: Origin provenance — session-scoped taint tracking](docs/adr/004-origin-provenance-tracking.md)
- [ADR-005: Deny + add rule — instant local pin, reviewed YAML suggestion](docs/adr/005-deny-add-rule.md)
- [ADR-006: Team Agent Trust — Slack / visibility mirror](docs/adr/006-team-agent-trust-slack-mirror.md)

## Docs

- [PRD](docs/PRD.md) ([中文](docs/PRD.zh.md))
- [Example policy](policies/default.yaml)

## Quick Start (v1 target)

```bash
# Policy engine
cd engine && pip install -r requirements.txt
python engine.py            # serves http://127.0.0.1:8787

# Wire the Claude Code hooks
cp adapters/claude-code/*.sh ~/.claude/hooks/
# register PreToolUse, PostToolUse, SessionStart, UserPromptSubmit in
# .claude/settings.json (see adapters/claude-code/README.md)

# Dashboard
npm install && npm run dev
```

## Environment Variables

```
FIREWALL_DB=sqlite:///./firewall.db
FIREWALL_POLICY=./policies/default.yaml
FIREWALL_FAIL_MODE=closed    # closed = block when engine unreachable (default)
APPROVAL_TIMEOUT_SECONDS=300 # pending approvals expire to deny
FIREWALL_TAINT_TTL_SECONDS=1800 # hard safety-net for session taint (ADR-004)
FIREWALL_DASHBOARD_ORIGIN=http://localhost:3000 # CORS allowlist for the Next.js UI
FIREWALL_SLACK_WEBHOOK_URL=  # optional Incoming Webhook for audit channel (ADR-006, fail-open)
```

## Team Agent Trust (ADR-006)

Visibility mirror for `@Claude` / team-agent actions — **no approval gate**:

```bash
# Record a mirror event (engine must be up)
cd engine && python cli.py mirror --summary "@Claude edited README in #eng" --agent "@Claude"

# Or:
echo '{"summary":"@Claude acted","agent_mention":"@Claude","notify":true}' \
  | ../adapters/slack/mirror.sh

# Dashboard: open /audit  ·  API: GET /decisions
```

See [adapters/slack/README.md](adapters/slack/README.md).

## Status

**Version:** 0.4.0 — Audit dashboard + `GET /decisions` + `POST /mirror` Team Agent Trust Slack visibility module (ADR-006). Approval queue unchanged.
