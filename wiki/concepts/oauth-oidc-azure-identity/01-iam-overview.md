# 01. Identity and Access Management Overview

Chinese: [01-iam-overview.zh.md](01-iam-overview.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).

This hub opens the Azure-oriented IAM track. Use the catalog below; do not treat Azure service names as “already implemented in XingAI.”

## Known

- OAuth answers API authorization; OIDC answers who authenticated — outline §1–§23 final rules (`raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`).
- XingAI teaching already separates wall #1 (OAuth scope) from wall #2 (business policy) — see [agent-governance-and-mcp](../agent-governance-and-mcp.md) and [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md).

## Missing

- This outline is Azure-centric pedagogy; XingAI public POCs often use custom AS / demo IdP, not Entra — wiring map is incomplete.
- No production Entra tenant evidence in this wiki snapshot.

## Rethink

- Treating “OAuth done” as “secure MCP” collapses Course 04’s confused-deputy lesson — scope ≠ settlement policy ([blog](https://github.com/xingaiapp/xingai-tech-blog/blob/main/posts/2026-07-13-mcp-auth-scope-is-not-policy-second-wall.md)).

## Debate

- Workforce Entra vs External ID CIAM for XingAI consumer apps — open product choice, not settled by this outline.

## Needs evidence

- Whether any XingAI product ships Entra External ID in production (Needs public deploy notes).

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
