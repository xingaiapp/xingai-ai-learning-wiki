# OAuth / OIDC / Azure Identity / API Security — curriculum outline

**Origin:** User-provided wiki outline (Cursor paste), 2026-07-16.
**Purpose:** Teaching spine from IAM basics through Azure Entra, APIM, MCP Resource Server, audit.

This file is the snapshot of the teaching outline. Living wiki pages under
`wiki/concepts/oauth-oidc-azure-identity/` synthesize it against XingAI public
MCP/OAuth materials — they are not a copy of this file.

## Final rules (from outline §23)

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
Scope → what you can do
Role → what role you are
Business Policy → whether this business object is allowed
Session → application login state
```

## Recommended wiki catalog (§24)

01 Identity and Access Management Overview
02 Authentication vs Authorization
03 OAuth 2.0 Fundamentals
04 OpenID Connect Fundamentals
05 ID Token vs Access Token
06 Authorization Code Flow with PKCE
07 State, Nonce, and PKCE
08 OAuth Token Types
09 JWT, Bearer, Opaque, and PoP Tokens
10 Scope, Role, and Business Authorization
11 OIDC Discovery and JWKS
12 Microsoft Entra ID Architecture
13 Azure App Registration
14 MSAL Integration
15 Azure API Management Security
16 Managed Identity and Workload Identity
17 On-Behalf-Of Flow
18 Session and Cookie Security
19 API Keys and PATs
20 OAuth/OIDC vs SAML
21 Microsoft Entra External ID
22 MCP Server Authentication and Authorization
23 Logging, Monitoring, and Auditing
24 Security Best Practices
25 Common Errors and Troubleshooting
26 Complete Azure Reference Architecture

## Section digests (§1–22)

### §1 AuthN vs AuthZ; OAuth; OIDC
- Authentication = who are you; Authorization = what may you do.
- OAuth 2.0 = authorization framework for API access (not a login protocol by itself).
- OIDC = OAuth 2.0 + standardized identity (`scope=openid`, ID Token, client session).

### §2 ID Token vs Access Token
- ID Token → Client/RP (login result). Access Token → Resource API/MCP.
- Never use ID Token to call APIs; never treat Access Token as login session.

### §3–4 Auth Code + PKCE; state/nonce/PKCE
- Phase A login → code+PKCE → tokens → session; Phase B Bearer to API + scope/role + business rules.
- state=CSRF/callback binding; nonce=ID Token binding; PKCE=code theft protection (S256).

### §5–6 Token types & formats
- Code / ID / Access / Refresh — distinct audiences.
- Bearer vs JWT format vs Opaque introspection vs sender-constrained (DPoP/mTLS).

### §7–8 Scope/Role/Policy; 401/403
- Scope=capability; Role=identity role; Business policy=object-level allow.
- 401=bad credential; 403=credential ok, permission denied.

### §9 Discovery + JWKS
- `/.well-known/openid-configuration`; Entra `login.microsoftonline.com/{tenant}/v2.0/...`
- Validate JWT via JWKS kid; do not hardcode signing keys.

### §10–15 Azure map
- Entra = IdP/AS/OP; APIM gateway; Key Vault; Managed Identity; App Registration (client vs API expose scopes); MSAL; APIM validate-jwt ≠ business authz; MI = service identity not end-user; OBO for middle-tier user delegation.

### §16–19 Session, API key/PAT, SAML, External ID
- Session cookie after ID Token verify (Secure/HttpOnly/SameSite).
- Prefer MI / WIF / OAuth over PAT; API key ≠ full identity.
- New apps: OIDC+OAuth; SAML for legacy SSO.
- External ID = CIAM; separate from workforce tenant; identity attrs vs business DB.

### §20–22 MCP + audit + practices
- MCP Server = Resource Server; MCP Client = OAuth Client.
- Checks: sig/iss/aud/exp/tid/scope/roles/tool/business/rate/audit — never log tokens.
- Client: Auth Code+PKCE+MSAL; API: validate + business authz; Infra: HTTPS, MI, Key Vault, short-lived tokens.
