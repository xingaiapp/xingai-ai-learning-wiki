# Concept: Agent Governance And MCP

Two related but distinct control questions that recur across courses and products:

1. **Can this caller invoke this tool at all?** — OAuth scope / MCP authorization ([Course 04](../courses/04-mcp-interoperability.md)).
2. **Is this specific action, right now, allowed?** — a business-rule policy layer independent of scope (dollar caps, claim-type allowlists, read-vs-write authority) ([Course 03](../courses/03-tool-use-ai-agents.md)'s `Validate → Approve/Execute` split).

This "two-wall" split is not academic — `claims-mcp-oauth-poc`'s ADR-006 was written specifically because scope alone can't express "this partner may not authorize settlements over $10,000." The [Third-Party MCP Access](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-07-15-third-party-mcp-auth-api-key-vs-oauth2.md) design article (written this session) generalizes the same reasoning into an API-key-vs-OAuth decision framework.

## Runtime vs. pre-production — a gap this session found and acted on

[xingai-agent-firewall](../products/xingai-agent-firewall.md) implements the *runtime* half of this concept (policy → risk score → approval → ledger, per live tool call, deterministic scoring — see that product page for why an LLM judge was deliberately rejected as the primary verdict mechanism). Nothing in the reviewed portfolio implemented the *pre-production* half — certifying a Skill/MCP tool's permissions and behavior before it's ever called live — until the 2026-07-16 Opportunity Radar review picked **Agent Skill Assurance & Evaluation** as an upgrade to `xingai-agent-firewall` specifically to close that gap. See [Review Findings](../syntheses/review-findings-2026-07-16.md).

**Also relevant:** Firewall's `PRODUCTION-READINESS.md`-style gap and [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.md)'s own flagged prompt-injection risk (on its free-text `loss_description` field) are the same underlying failure class — untrusted content steering an agent/LLM's decision — addressed in two separate products, with neither currently covering the other.

## Connects to

- [Course 03](../courses/03-tool-use-ai-agents.md), [Course 04](../courses/04-mcp-interoperability.md), [Course 05](../courses/05-agent-runtime-multi-agent.md)
- [Concept: Decision Ledger pattern](decision-ledger-pattern.md) — every governance verdict in this concept is itself a Decision Ledger row.

## Sources

`raw/courses/03-tool-use-ai-agents.md`, `raw/courses/04-mcp-interoperability.md`; cross-repo claims from chat analysis during the 2026-07-16 review and Opportunity Radar session, not a single raw file.
