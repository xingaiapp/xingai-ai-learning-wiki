# Course 04: MCP And Interoperability

**Prerequisite:** [03](03-tool-use-ai-agents.md) · **Gate:** secured MCP client/server lab · **Next:** [05](05-agent-runtime-multi-agent.md)

MCP as a governed capability boundary, not just a plugin format: initialize → discover → validate → authenticate → authorize-for-target-resource → execute least-privilege → audit. The failure list — never pass through upstream tokens, never accept a token meant for another resource, never infer authorization from tool visibility — is the confused-deputy risk that `claims-mcp-oauth-poc`'s two-wall model (OAuth scope + independent business-rule policy, see [ADR-006](../../../xingai-enterprise-ai-pocs/docs/adr/006-claims-mcp-oauth-poc-real-auth.md) in that repo) was built specifically to close.

The course lab extends an existing lab (`guides/2026-07-12-mcp-oauth-pkce-lab.md`) rather than building from scratch — matches this wiki's own principle of not re-deriving what already exists.

## Connects to

- [Concept: Agent governance and MCP](../concepts/agent-governance-and-mcp.md)
- `claims-workflow-v2-poc`'s hand-rolled JSON-RPC-over-FastAPI MCP server (reviewed extensively this session — Phase 1 of its ADR-009) is a working, if deliberately simplified, instance of this course's architecture: a static service token today, scopes pre-named (`policy.read`, `payments.write`) to match a real Authorization Server later without a redesign.
- The **[Agent Skill Assurance & Evaluation](../products/opportunity-radar.md)** opportunity (this session's Opportunity Radar pick, 2026-07-16) is exactly the *pre-production* counterpart to this course's runtime authorization discipline — it certifies a tool/Skill before the capability-negotiation handshake this course teaches ever happens live.

## Verified

`modelcontextprotocol.io/specification/2025-11-25/basic/authorization` and `a2a-protocol.org/latest/specification/` both confirmed as real, resolving primary sources via web search on 2026-07-16. ZH sibling ingested 2026-07-16: Python code byte-identical, heading count matches (7/7).

## Sources

`raw/courses/04-mcp-interoperability.md`
