# ADR-001: Interception Point — Harness Hooks First, MCP Gateway Later

**Date:** 2026-07-05
**Status:** Accepted
**Author:** Xing @ XingAI
**Also available:** [中文](001-interception-point.zh.md)

## Context

An agent firewall is only as good as its interception point. If the agent can reach the shell, filesystem, or network without passing through the policy layer, the firewall is decoration. Three candidate architectures:

1. **Harness hooks** — the agent runtime (Claude Code, Agent SDK) exposes lifecycle hooks (`PreToolUse`) that run *before* a tool call executes and can block it. The firewall becomes a hook script calling a local policy service.
2. **MCP gateway proxy** — all tools are served through a gateway MCP server that wraps real tools and applies policy before forwarding. Covered conceptually in xingai-enterprise-ai-design's "orchestrator vs MCP gateway" article.
3. **OS-level sandbox/proxy** — seccomp/sandbox-exec/network proxy under the agent process. Strongest guarantee, highest build cost, platform-specific.

Constraints: solo builder, v1 must demo in weeks not months, the demo target is Claude Code (where the 0din attack was shown), and the enforcement guarantee must be honest — we document what each layer does and does not stop.

## Decision

**v1 intercepts via harness hooks (Claude Code `PreToolUse`), calling a local FastAPI policy service synchronously. The MCP gateway proxy is the committed phase-2 path for enterprise/multi-agent deployments. OS-level sandboxing stays out of scope.**

The hook adapter is thin: serialize the pending tool call (tool name, input, cwd, session id) → POST to `http://127.0.0.1:8787/check` → exit code enforces the verdict (0 = allow, non-zero = block with reason on stderr). Fail-closed by default: if the engine is unreachable, gated categories are blocked (`FIREWALL_FAIL_MODE=closed`).

## Consequences

Positive:
- Fastest honest demo: works with the real Claude Code today, no forked runtime, no custom agent.
- The policy engine is adapter-agnostic — the same `/check` API serves the phase-2 MCP gateway and any other harness that grows hooks.
- Synchronous verdict fits the approval workflow (ADR-003): "review" verdicts hold the call open while the human decides.

Tradeoffs:
- Hooks are opt-in per machine/project config — a user (or attacker with settings write access) can remove the hook. v1 protects against *tricked agents*, not *malicious local users*. Stated plainly in README and docs.
- Coverage is per-harness: only Claude Code at v1. Cursor/Devin/other agents need their own adapters or must wait for the MCP gateway.
- Hook latency budget: policy check must stay under ~200ms p95 or it degrades the agent UX; deterministic rules (ADR-002) keep this feasible.

Risks:
- Harness hook API changes upstream → adapter is isolated in `adapters/claude-code/`, engine untouched; pin against documented hook contract.
- False sense of security if users assume OS-level guarantees → threat-model section in PRD explicitly scopes what v1 enforces.

## Alternatives Considered

| Option | Reason rejected |
|---|---|
| MCP gateway first | Requires routing all tools through the gateway — real coverage only for MCP tools, while the riskiest calls (Bash, file writes) are native harness tools in Claude Code; hooks cover exactly those. Gateway remains phase 2 where it fits (enterprise fleets, non-hook harnesses). |
| OS-level sandbox first | Months of platform-specific work (macOS sandbox-exec vs Linux seccomp), kills the demo timeline; also duplicates what harness sandboxing already provides. |
| LLM-side guardrails (system-prompt rules only) | Not enforcement — the 0din exploit works precisely because instructions can be injected around model-level rules. |

## Migration Triggers

- A second harness needs coverage → build the MCP gateway adapter (phase 2), same engine.
- Enterprise deployment with untrusted local users → revisit OS-level enforcement as phase 3, likely by integrating an existing sandbox rather than building one.

## Related

- [ADR-002: Risk Scoring Model](./002-risk-scoring-model.md)
- [ADR-003: Approval Workflow + Decision Ledger](./003-approval-workflow-ledger.md)
- xingai-enterprise-ai-design: `articles/2026-06-13-orchestrator-vs-mcp-gateway.md`
- xingai-invest-decision-engine ADR-014 (read-only MCP) — same "gate the dangerous surface" discipline
