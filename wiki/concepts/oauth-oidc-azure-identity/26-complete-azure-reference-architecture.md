# 26. Complete Azure Reference Architecture

Chinese: [26-complete-azure-reference-architecture.zh.md](26-complete-azure-reference-architecture.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- Reference story from outline: User/Agent → Entra → Access Token → Client → (APIM) → MCP/API; MI for data plane; Key Vault for secrets; Monitor/Sentinel for audit (§10,§13–15,§20–21).
- Teaching architecture only — not a verified XingAI production topology.

## Missing

- No single diagram artifact in raw; no capacity/cost model.

## Rethink

- Copy-pasting this stack into every POC fights portability of OSS teaching repos.

## Debate

- Minimal portable subset (AS+RS+PKCE+policy) vs full Azure suite.

## Needs evidence

- Publish a Mermaid diagram in a follow-up ingest if desired.

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
