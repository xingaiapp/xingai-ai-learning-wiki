# OAuth, OIDC, Azure Identity & API Security

Chinese: [00-overview.zh.md](00-overview.zh.md)

Wiki synthesis of **[Course 10](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/README.md)** in `xingai-enterprise-ai-design`. Pages carry the course teach block (5W + diagram + minimal check), then critique gaps against XingAI public MCP/OAuth materials.

**Not** a paste of the old external outline. Outline history remains under `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/` for provenance only.

**Course hub (wiki):** [10-oauth-oidc-azure-identity](../../courses/10-oauth-oidc-azure-identity.md)  
**Raw snapshot:** `raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/`

**No UX PNG** (identity theory / Azure mapping; no product chrome).

## How to read

1. Protocol: [02 AuthN vs AuthZ](02-authentication-vs-authorization.md) → [05 ID vs Access Token](05-id-token-vs-access-token.md) → [06 Code + PKCE](06-authorization-code-flow-pkce.md) → [10 Scope / business](10-scope-role-business-authorization.md).
2. Azure mapping: [12 Entra](12-microsoft-entra-id-architecture.md) through [21 External ID](21-microsoft-entra-external-id.md) — portable OIDC terms first.
3. Agents/ops: [22 MCP AuthN/AuthZ](22-mcp-server-authn-authz.md) + [agent-governance-and-mcp](../agent-governance-and-mcp.md) + [Course 04](../../courses/04-mcp-interoperability.md).
4. Lab gate: [PKCE MCP lab](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.md).

## Final rules (Course 10)

```text
OAuth → API authorization
OIDC → user login
ID Token → Client
Access Token → API / MCP Server
Refresh Token → Authorization Server
Authorization Code → Token Endpoint
state → protect callback
nonce → protect ID Token
PKCE → protect Authorization Code
Scope → what you can do (capability)
Role → what role you are
Business Policy → whether this business object is allowed
Session → application login state
```

## Catalog

| # | Page |
|---|---|
| [01](01-iam-overview.md) | Identity and Access Management Overview |
| [02](02-authentication-vs-authorization.md) | Authentication vs Authorization |
| [03](03-oauth-2-fundamentals.md) | OAuth 2.0 Fundamentals |
| [04](04-openid-connect-fundamentals.md) | OpenID Connect Fundamentals |
| [05](05-id-token-vs-access-token.md) | ID Token vs Access Token |
| [06](06-authorization-code-flow-pkce.md) | Authorization Code Flow with PKCE |
| [07](07-state-nonce-and-pkce.md) | State, Nonce, and PKCE |
| [08](08-oauth-token-types.md) | OAuth Token Types |
| [09](09-jwt-bearer-opaque-pop.md) | JWT, Bearer, Opaque, and PoP Tokens |
| [10](10-scope-role-business-authorization.md) | Scope, Role, and Business Authorization |
| [11](11-oidc-discovery-and-jwks.md) | OIDC Discovery and JWKS |
| [12](12-microsoft-entra-id-architecture.md) | Microsoft Entra ID Architecture |
| [13](13-azure-app-registration.md) | Azure App Registration |
| [14](14-msal-integration.md) | MSAL Integration |
| [15](15-azure-api-management-security.md) | Azure API Management Security |
| [16](16-managed-identity-workload-identity.md) | Managed Identity and Workload Identity |
| [17](17-on-behalf-of-flow.md) | On-Behalf-Of Flow |
| [18](18-session-and-cookie-security.md) | Session and Cookie Security |
| [19](19-api-keys-and-pats.md) | API Keys and PATs |
| [20](20-oauth-oidc-vs-saml.md) | OAuth/OIDC vs SAML |
| [21](21-microsoft-entra-external-id.md) | Microsoft Entra External ID |
| [22](22-mcp-server-authn-authz.md) | MCP Server Authentication and Authorization |
| [23](23-logging-monitoring-auditing.md) | Logging, Monitoring, and Auditing |
| [24](24-security-best-practices.md) | Security Best Practices |
| [25](25-common-errors-troubleshooting.md) | Common Errors and Troubleshooting |
| [26](26-complete-azure-reference-architecture.md) | Complete Azure Reference Architecture |

## Known

- Course 10 published in public `xingai-enterprise-ai-design` with 26 bilingual modules + hub (snapshotted under `raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/`).
- Runnable teaching path already existed: [PKCE lab](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.md) + [Course 04](../../courses/04-mcp-interoperability.md) + [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md) two-wall model.

## Missing

- Live Entra tenant screenshots / APIM policy XML / MSAL samples inside Course 10 modules.
- Portable Fly/Vercel twin of Module 26’s Azure reference diagram.

## Rethink

- Older wiki pages that only cited the external outline under-taught diagrams and fail-closed checks — rewritten against Course 10.
- “OAuth integrated” without business policy still fails the two-wall bar.

## Debate

- Keep Course 10 as specialization vs promote it onto the hiring ladder as Level 10.
- Entra-first vs IdP-portable defaults for public XingAI repos.

## Needs evidence

- Which XingAI production/demo apps use Entra External ID, MSAL, or APIM today.

## Sources

- [Course 10 README](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/README.md)
- `raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/`
- Provenance outline (superseded as teaching source): `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/`
