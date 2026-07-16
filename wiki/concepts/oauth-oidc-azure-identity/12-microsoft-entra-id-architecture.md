# 12. Microsoft Entra ID Architecture

Chinese: [12-microsoft-entra-id-architecture.zh.md](12-microsoft-entra-id-architecture.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- Entra maps to IdP / Authorization Server / OpenID Provider; RS may be API/MCP; APIM/Key Vault/MI/Sentinel listed (§10).
- This is a **mapping table for teaching**, not a claim that XingAI deploys all of these.

## Missing

- No XingAI production architecture diagram using full Entra stack in raw.

## Rethink

- Equating “Azure” with “enterprise-ready” without two-wall policy — Rethink.

## Debate

- Entra vs non-Microsoft IdP for XingAI OSS POCs meant to stay portable.

## Needs evidence

- Any public XingAI repo with Entra app registration screenshots (UX) — none attached this ingest.

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
