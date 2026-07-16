# 19. API Keys and PATs

Chinese: [19-api-keys-and-pats.zh.md](19-api-keys-and-pats.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).  
**Primary teaching source:** [Course 10 · Module 19](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/19-api-keys-and-pats.md) · [hub](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/README.md)

## Teach (from Course 10)

- **What:** API keys and personal access tokens are shared secrets. They authenticate a caller but usually lack user consent UX and fine-grained OAuth scopes.
- **Why:** wrong identity boundaries create confused-deputy and silent over-privilege failures.
- **Who:** internal automation, partner integrations under contract.
- **When:** prefer OAuth for third-party and user-delegated access; keys only with rotation, scoped vaults, and monitoring.
- **Where:** identity and policy sit at trust boundaries between clients, IdPs, APIs, and tools.
- **How:** learn the vocabulary, draw the sequence, implement the minimal check, then fail closed on mismatch.

### Diagram

```mermaid
flowchart LR
    Key[API key / PAT] --> Secret[Shared secret risk]
    OAuth[OAuth + PKCE] --> Consent[Consent + scopes + revocation]
```

### Minimal check

```python
def prefer_oauth(third_party: bool, user_delegated: bool) -> str:
    return "oauth" if third_party or user_delegated else "key_with_controls"
assert prefer_oauth(True, False) == "oauth"
```

### Failure modes (course)

- Confusing login success with authorization.
- Sending the wrong token type to the wrong audience.
- Skipping PKCE, state, nonce, or exact redirect checks.
- Encoding business policy only in prompts or UI visibility.

## Known

- Course 10 Module 19 defines the vocabulary, diagram, and fail-closed checks above (`raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/modules/19-api-keys-and-pats.md`; public: [module](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/19-api-keys-and-pats.md)).
- Hands-on OAuth/PKCE path: [PKCE MCP lab](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.md) · [auth deep dive](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-auth-deep-dive.md).
- Cross-links: [agent-governance-and-mcp](../agent-governance-and-mcp.md) · [Course 04](../../courses/04-mcp-interoperability.md) · [Course 10 wiki](../../courses/10-oauth-oidc-azure-identity.md) · [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md).

## Missing

- No live Entra tenant screenshots for “API Keys and PATs” — course treats Azure as a mapping, not a required cloud.

## Rethink

- Entra vocabulary must map back to portable OIDC/OAuth terms or OSS POCs drift.

## Debate

- Entra-first teaching vs IdP-portable teaching for public XingAI repos.

## Needs evidence

- Which public XingAI apps actually use this Azure control (if any).

## Sources

- Course: [API Keys and PATs](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/19-api-keys-and-pats.md) · [中文](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/19-api-keys-and-pats.zh.md)
- Snapshot: `raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/modules/19-api-keys-and-pats.md`
- Lab: [OAuth 2.1 + PKCE MCP](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.md)
