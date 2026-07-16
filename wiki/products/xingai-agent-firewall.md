# Product: xingai-agent-firewall

**Version at last check (2026-07-16):** 0.4.0 · **Threat model:** a *tricked* coding agent (prompt-injected via untrusted content), not a malicious local user or supply-chain compromise of the firewall itself.

Every agent tool call passes through: policy check → risk score → approval → ledger. Built in direct response to Mozilla 0din's demonstration that a clean-looking GitHub repo can trick Claude Code into running malicious commands — the agent's helpfulness *is* the attack surface. The fix is architectural (a policy layer between the agent and the world), not model-level.

This is the runtime half of [Concept: Agent governance and MCP](../concepts/agent-governance-and-mcp.md); the **Agent Skill Assurance & Evaluation** opportunity picked in this session's Opportunity Radar review is the pre-production half this product doesn't yet have — see that concept page for the full reasoning.

## How verdicts are actually produced (ADR-002) — deterministic, not an LLM judge

The verdict (`allow | deny | review`) always comes from weighted deterministic rules — never an LLM. Reasoning, verified against the raw ADR: an LLM judge is itself prompt-injectable by the exact content it's inspecting, so "a firewall whose judge can be prompt-injected inherits the vulnerability it exists to stop." An optional LLM classifier can add one advisory signal (capped weight ≤15) but can never override a deny, and is off by default. Seven named signals (`shell_pipe_from_network`=40, `secrets_path_access`=35, `write_outside_workspace`=25, `network_unknown_host`=20, `untrusted_origin_instruction`=20, `destructive_command`=25, `privilege_escalation`=30) sum to a 0-100 score; thresholds (<25 allow, 25-69 review, ≥70 deny) are config, not code.

## How it knows content is untrusted (ADR-004) — session-scoped taint, not per-call tracing

The interesting engineering decision here: the naive "trace which string caused this call" isn't available at the Claude Code hooks boundary, so the actual mechanism is a **session-scoped taint window**, not a time or call-count window (both alternatives were considered and rejected as arbitrary — see the raw ADR's Alternatives table). `SessionStart` snapshots a git-tracked-files baseline; any `Read`/`Grep`/`Glob` of a path outside that baseline, or any `WebFetch`/`WebSearch` result (always untrusted, no baseline possible), taints the session until the next `UserPromptSubmit` clears it — bounded by the conversational turn, which is exactly the shape of the actual 0din attack (read untrusted content, then act on it later in the same turn). Honest documented gap: non-git working directories get no file-level provenance protection at all, only the always-untrusted web-fetch rule.

## Connects to

- [Course 03](../courses/03-tool-use-ai-agents.md) — this product is a real, generalized instance of that course's `Validate → Approve/Execute` state diagram, applied to *any* tool call, not one demo loop.
- [Concept: Agent governance and MCP](../concepts/agent-governance-and-mcp.md), [Concept: Decision Ledger pattern](../concepts/decision-ledger-pattern.md) — every verdict is a ledger row (`engine/ledger.py`).
- [claims-workflow-v2-poc](claims-workflow-v2-poc.md) — its `PRODUCTION-READINESS.md` flags prompt-injection risk on a free-text field as unaddressed; this product's whole existence is the general-purpose answer to that same risk class, just not yet wired to that specific POC.
- **Agent Skill Assurance & Evaluation** (this session's Opportunity Radar pick, 2026-07-16) — the recommended upgrade path for this exact repo, adding a pre-production `skills/` module that reuses `engine/ledger.py` and `engine/policy.py` rather than forking a second governance surface. See `xingai-opportunity-radar/agents/out/latest.en.md` for the full Decision Card (not yet ingested into this wiki as a raw file — see the opportunity-radar product page).

## Sources

`raw/xingai-agent-firewall/README.md`, `docs/PRD.md`, `docs/adr/001-interception-point.md` through `006-team-agent-trust-slack-mirror.md`
