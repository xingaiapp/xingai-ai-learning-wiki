# Product: event-bus-ai-review

Chinese: [event-bus-ai-review.zh.md](event-bus-ai-review.zh.md)

**Repo:** [xingai-enterprise-ai-pocs](https://github.com/xingaiapp/xingai-enterprise-ai-pocs) · **Status:** Architecture only — not runnable

Design for routing a business event to independent subscribers (AI review, compliance, human approval, audit) via an event bus, then assembling a decision packet.

## What the README won't emphasize

Every other multi-agent POC in this wiki is a **synchronous supervisor graph** (lab, RAG, workflow-v2). This one asks: what if AI review and compliance must not share a call stack? That is a control-plane choice, not a "more agents" choice.

Use it as contrast when Course 05/06 talk about durable execution and human-in-the-loop — the same requirements can land as LangGraph nodes *or* as bus subscribers. ADR-004 marks it placeholder; do not pretend there is code to verify.

## Connects to

- [Concept: Decision Ledger pattern](../concepts/decision-ledger-pattern.md), [Concept: Loop engineering](../concepts/loop-engineering.md)
- [Claims POC family](../syntheses/claims-poc-family-tradeoffs.md) (odd one out section)

## Sources

`raw/pocs/event-bus-ai-review/README.md`, `architecture.md`; `raw/pocs/docs/adr/004-event-bus-ai-review-placeholder.md`
