# Product: claims-partner-api-mcp-poc

**Repo:** [xingai-enterprise-ai-pocs](https://github.com/xingaiapp/xingai-enterprise-ai-pocs) · **Status:** Runnable · Phase 1

OpenAPI-first wrap of a claims REST API as one MCP server with broad coverage (~18 tools / 7 domains), Zod-validated inputs, idempotent payment writes, and an explicit claim-status state machine. Auth for third parties is **intentionally missing**.

## What the README won't emphasize

This is the other half of a controlled experiment with [claims-mcp-oauth-poc](claims-mcp-oauth-poc.md). If you only study oauth, you overfit to tiny surfaces. If you only study this, you ship partner-facing tools with a shared static token and call it done. ADR-007 says the quiet part: full coverage now, auth layer later — combine with the oauth POC's scopes, don't invent a third auth story.

Money-moving tools (`claims_create_payment`, status transitions) carry `destructiveHint` and idempotency keys. That is Course 03's consequential-action discipline applied to tool metadata, not to an LLM judge.

## Where it sits in the family

Workflow-v2's MCP surface stays small (policy / ledger / payments) because its experiment is orchestration + audit, not partner API sprawl. Partner-api is the sprawl experiment. See [Claims POC family](../syntheses/claims-poc-family-tradeoffs.md).

## Connects to

- [Concept: Agent governance and MCP](../concepts/agent-governance-and-mcp.md), [Course 04](../courses/04-mcp-interoperability.md)
- Article: [MCP API coverage vs workflow tools](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-07-13-mcp-api-coverage-vs-workflow-tools.md)

## Sources

`raw/pocs/claims-partner-api-mcp-poc/README.md`, `architecture.md`; `raw/pocs/docs/adr/007-claims-partner-api-mcp-poc-full-coverage.md`
