# PRD — XingAI Agent Firewall

**Date:** 2026-07-05 · **Status:** Draft v1 · **Author:** Xing @ XingAI · **中文版:** [PRD.zh.md](./PRD.zh.md)

## 1. Problem

AI coding agents execute shell commands, write files, and reach the network with a speed and confidence no human reviewer matches. Mozilla 0din demonstrated that a clean-looking GitHub repository can steer Claude Code into running malicious commands — prompt injection through content the agent was *supposed* to read. Model-level guardrails cannot close this: the injection rides in through the front door.

Enterprises adopting agents have no equivalent of a network firewall for agent actions: no policy layer, no approval workflow, no audit trail answering "what did the agent try to do, who allowed it, and why."

## 2. Users

| User | Need |
|---|---|
| **Solo builder running coding agents** (v1 primary) | Don't get owned by a poisoned repo; see what the agent almost did |
| **Enterprise architecture / platform team** (phase 2) | Fleet-wide policy, approval roles, compliance-grade audit export |
| **Security team** (phase 2) | Risk trends, override analytics, incident reconstruction from ledger |

## 3. Threat Model (v1 — stated honestly)

**In scope:** a *tricked agent* — prompt-injected instructions from untrusted content (repos, web pages, docs) causing dangerous tool calls: network-to-shell pipes, credential reads, out-of-workspace writes, destructive commands, unknown-host egress.

**Out of scope at v1:** a malicious local user (can remove the hook), kernel/OS-level escapes, supply-chain compromise of the firewall itself, non-Claude-Code harnesses. See ADR-001.

## 4. MVP Scope (4 features)

1. **Policy engine** — FastAPI service, `/check` endpoint, YAML rules → verdict (`allow|deny|review`) + risk score 0–100 with fired-signal explanation. Deterministic (ADR-002). p95 < 200ms.
2. **Claude Code adapter** — `PreToolUse` hook script; fail-closed; blocks with human-readable reason on stderr (ADR-001). `SessionStart`/`PostToolUse`/`UserPromptSubmit` hooks feed origin provenance so `untrusted_origin_instruction` is a real signal, not a test-only parameter (ADR-004).
3. **Approval queue** — dashboard page listing held `review` calls; one-click Approve once / Approve for session / Deny / Deny + add rule; timeout → deny (ADR-003).
4. **Ledger + audit view** — every intercepted call is one Decision row (shared XingAI schema); dashboard shows history, filterable by verdict/category/session; per-rule override rate.

**Demo milestone:** reproduce a 0din-class attack in a sandboxed repo and show the firewall catching it live — intercepted, scored, queued, logged.

## 5. Non-Goals (v1)

- No MCP gateway (phase 2, ADR-001), no OS sandboxing (phase 3)
- No multi-user auth / roles — single operator, local-first
- No LLM judge in the verdict path (advisory channel exists, off by default — ADR-002)
- No cloud service; nothing leaves the machine

## 6. Success Metrics

| Metric | Target |
|---|---|
| 0din-reproduction corpus caught | 100% (regression suite) |
| Benign-corpus false `review` rate | < 5% of calls (npm install, git commit, pytest…) |
| Policy check latency | p95 < 200ms |
| Time-to-decision in approval queue | median < 15s (context is good enough to decide fast) |

## 7. Architecture

```
Claude Code session
  ↓ SessionStart hook ──────► POST /session/init (git ls-files baseline, ADR-004)
  ↓ PostToolUse hook ───────► POST /taint (Read/Grep/Glob/WebFetch/WebSearch, ADR-004)
  ↓ UserPromptSubmit hook ──► POST /taint/clear (new turn, ADR-004)
  ↓ PreToolUse hook (adapters/claude-code)
  ↓ POST /check ────────────► FastAPI policy engine
                                ├─ YAML policy (policies/*.yaml)
                                ├─ signal matchers + scorer (origin derived from session taint)
                                ├─ SQLite (WAL): decisions, approvals, session allowlists, taint
                                └─ verdict: allow | deny | review(hold)
  ↑ exit 0 (allow) / exit 2 + reason (deny)        ▲
                                                   │ approve/deny
Next.js dashboard ── reads SQLite ── approval queue + audit views
```

Follows the XingAI worker-architecture standard with one deliberate deviation: the policy check is synchronous (a firewall cannot be eventually consistent). The dashboard remains cache-reading per standard.

## 8. Milestones

| Week | Deliverable |
|---|---|
| 1 | Engine skeleton + signal matchers + regression corpus; hook adapter blocking for real; origin provenance (ADR-004): session baseline + turn-scoped taint tracking, so `untrusted_origin_instruction` fires on real 0din-class input instead of only in tests |
| 2 | Approval queue UI + session allowlists + timeout-to-deny |
| 3 | Audit views + override-rate stats; 0din live demo recorded |
| 4 | Blog post ("Your coding agent's helpfulness is the attack surface") + polish + publish |
