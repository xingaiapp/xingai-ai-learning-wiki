# ADR-006: Team Agent Trust — Slack / Visibility Mirror

**Date:** 2026-07-14
**Status:** Accepted
**Author:** Xing @ XingAI
**Also available:** [中文](006-team-agent-trust-slack-mirror.zh.md)

## Context

Opportunity Radar Issue #2 / Project Pick selected **Team Agent Reliability Layer** as an **upgrade of Agent Firewall**, not a new `*.xingai.app`. The two-week MVP is a Slack (or team-agent) **visibility log**: when an agent like `@Claude` acts, write a one-line audit entry. Approval gating stays on the existing `/check` path — this module must not invent a second product or a second ledger.

## Decision

1. **Ledger remains source of truth.** New rows use domain `team-agent-mirror` and recommendation `mirror` via `ledger.record_mirror_event` / `POST /mirror`.

2. **Read API for audit UI:** `GET /decisions` lists recent Decision rows (any domain). Dashboard page `/audit` polls it.

3. **Slack adapter** lives under `adapters/slack/` (ADR-001 thin adapter). Inbound helpers POST `/mirror`. Outbound uses Incoming Webhook (`FIREWALL_SLACK_WEBHOOK_URL`) via `engine/notify.py`.

4. **Fail-open notify.** Missing webhook or HTTP errors never block `/mirror` or agents. Contrast with PreToolUse fail-closed.

5. **No approval hold on `/mirror`.** Visibility only; Deny/Approve UI unchanged.

## Consequences

Positive: Team Agent Trust lands as a Firewall module (portfolio bet honored); audit gap from README closes.  
Tradeoff: full Slack Events verification is deferred; v1 accepts trusted local POSTs / scripts.

## Related

- [ADR-001](./001-interception-point.md) · [ADR-003](./003-approval-workflow-ledger.md)
- [adapters/slack/README.md](../../adapters/slack/README.md)
- Radar Project Pick: `xingai-opportunity-radar` ADR-005 + Issue 2026-06-28
