# MCP vs A2A vs ACP: How AI Agents Actually Talk to Each Other

(User paste, 2026-07-19. Image mentioned in paste but not attached.)

Agents are capable on their own. Combined with tools and other agents, their capabilities compound. But how should they communicate?

## MCP: agent to tool communication

The host app receives the user request, its embedded MCP client formats and routes it to the right MCP server, the server executes the tool call and returns a structured response. The agent uses the result to continue reasoning.

## A2A: agent to agent communication

An agent that can't complete a task alone discovers a capable peer via its Agent Card (published at a well-known URL), delegates the task, and receives a structured result back. If the second agent needs more input mid-task, it pauses in the input-required state and loops back to the first.

## ACP: agent to agent communication over REST (merged into A2A)

ACP took a REST-first approach. Peers were discovered through an Agent Manifest, called directly over HTTP, and responded to sync for low-latency tasks or via async SSE stream.

## Production framing (paste)

In production, MCP and A2A are complementary. MCP handles tool access, A2A handles agent communication.
