# 26. Complete Azure Reference Architecture

Chinese: [26-complete-azure-reference-architecture.zh.md](26-complete-azure-reference-architecture.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).  
**Primary teaching source:** [Course 10 · Module 26](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/26-complete-azure-reference-architecture.md) · [hub](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/README.md)

## Teach (from Course 10)

- **What:** A reference shape: Entra (workforce or External ID) + MSAL clients + APIM edge + APIs with managed identity + optional MCP resource server with two-wall authz.
- **Why:** wrong identity boundaries create confused-deputy and silent over-privilege failures.
- **Who:** enterprise architects, CTOs evaluating Azure-centric stacks.
- **When:** teaching and Azure-standard shops — portable OIDC/OAuth designs remain valid without APIM.
- **Where:** identity and policy sit at trust boundaries between clients, IdPs, APIs, and tools.
- **How:** learn the vocabulary, draw the sequence, implement the minimal check, then fail closed on mismatch.

### Diagram

```mermaid
flowchart TB
    User --> MSAL[MSAL app]
    MSAL --> Entra[Entra ID / External ID]
    MSAL --> APIM[APIM JWT validate]
    APIM --> API[API + business policy]
    API --> MI[Managed identity]
    MI --> Azure[Key Vault / data]
    Host[MCP Host] --> Entra
    Host --> MCP[MCP Server resource]
    MCP --> Policy[Scope + business policy + ledger]
```

### Minimal check

```python
components = ["entra", "msal", "apim_optional", "api_policy", "managed_identity", "mcp_two_wall"]
assert "mcp_two_wall" in components and "apim_optional" in components
```

### Failure modes (course)

- Confusing login success with authorization.
- Sending the wrong token type to the wrong audience.
- Skipping PKCE, state, nonce, or exact redirect checks.
- Encoding business policy only in prompts or UI visibility.

## Known

- Course 10 Module 26 defines the vocabulary, diagram, and fail-closed checks above (`raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/modules/26-complete-azure-reference-architecture.md`; public: [module](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/26-complete-azure-reference-architecture.md)).
- Hands-on OAuth/PKCE path: [PKCE MCP lab](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.md) · [auth deep dive](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-auth-deep-dive.md).
- Cross-links: [agent-governance-and-mcp](../agent-governance-and-mcp.md) · [Course 04](../../courses/04-mcp-interoperability.md) · [Course 10 wiki](../../courses/10-oauth-oidc-azure-identity.md) · [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md).

## Missing

- Operational depth for “Complete Azure Reference Architecture” is checklist-level; SIEM/runbook artifacts are not in Course 10.

## Rethink

- MCP two-wall + decision ledger are XingAI’s durable audit story — Azure APIM alone is not enough.

## Debate

- Azure reference architecture vs a portable Fly/Vercel twin diagram for XingAI demos.

## Needs evidence

- Public deploy diagram that matches a real XingAI status/API topology.

## Sources

- Course: [Complete Azure Reference Architecture](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/26-complete-azure-reference-architecture.md) · [中文](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/26-complete-azure-reference-architecture.zh.md)
- Snapshot: `raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/modules/26-complete-azure-reference-architecture.md`
- Lab: [OAuth 2.1 + PKCE MCP](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.md)
