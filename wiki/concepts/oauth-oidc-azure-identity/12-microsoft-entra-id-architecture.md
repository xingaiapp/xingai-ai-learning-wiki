# 12. Microsoft Entra ID Architecture

Chinese: [12-microsoft-entra-id-architecture.zh.md](12-microsoft-entra-id-architecture.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).  
**Primary teaching source:** [Course 10 · Module 12](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/12-microsoft-entra-id-architecture.md) · [hub](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/README.md)

## Teach (from Course 10)

- **What:** Entra ID is Microsoft's cloud directory and identity platform: tenants, apps, users, groups, conditional access.
- **Why:** wrong identity boundaries create confused-deputy and silent over-privilege failures.
- **Who:** Azure/enterprise architects, IdP admins.
- **When:** when the organization standardizes on Microsoft identity; map concepts to portable OIDC terms.
- **Where:** identity and policy sit at trust boundaries between clients, IdPs, APIs, and tools.
- **How:** learn the vocabulary, draw the sequence, implement the minimal check, then fail closed on mismatch.

### Diagram

```mermaid
flowchart TB
    Tenant[Entra tenant] --> Apps[App registrations]
    Tenant --> Users[Users / groups]
    Apps --> Tokens[OIDC/OAuth tokens]
    Users --> CA[Conditional Access]
```

### Minimal check

```python
mapping = {"entra_app": "oidc_client_or_resource", "tenant": "issuer_authority"}
assert mapping["tenant"] == "issuer_authority"
```

### Failure modes (course)

- Confusing login success with authorization.
- Sending the wrong token type to the wrong audience.
- Skipping PKCE, state, nonce, or exact redirect checks.
- Encoding business policy only in prompts or UI visibility.

## Known

- Course 10 Module 12 defines the vocabulary, diagram, and fail-closed checks above (`raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/modules/12-microsoft-entra-id-architecture.md`; public: [module](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/12-microsoft-entra-id-architecture.md)).
- Hands-on OAuth/PKCE path: [PKCE MCP lab](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.md) · [auth deep dive](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-auth-deep-dive.md).
- Cross-links: [agent-governance-and-mcp](../agent-governance-and-mcp.md) · [Course 04](../../courses/04-mcp-interoperability.md) · [Course 10 wiki](../../courses/10-oauth-oidc-azure-identity.md) · [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md).

## Missing

- No live Entra tenant screenshots for “Microsoft Entra ID Architecture” — course treats Azure as a mapping, not a required cloud.

## Rethink

- Entra vocabulary must map back to portable OIDC/OAuth terms or OSS POCs drift.

## Debate

- Entra-first teaching vs IdP-portable teaching for public XingAI repos.

## Needs evidence

- Which public XingAI apps actually use this Azure control (if any).

## Sources

- Course: [Microsoft Entra ID Architecture](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/12-microsoft-entra-id-architecture.md) · [中文](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/12-microsoft-entra-id-architecture.zh.md)
- Snapshot: `raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/modules/12-microsoft-entra-id-architecture.md`
- Lab: [OAuth 2.1 + PKCE MCP](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.md)
