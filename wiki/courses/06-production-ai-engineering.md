# Course 06: Production AI Engineering

**Prerequisite:** [05](05-agent-runtime-multi-agent.md) · **Gate:** production-readiness review · **Next:** [07](07-enterprise-decision-systems.md)

"A demo proves possibility; production evidence proves acceptable behavior under realistic load and failure." The release-gate code (`task_success >= 0.90`, `unsafe_action_rate == 0`, latency and cost thresholds) is a formalized version of exactly the kind of gap analysis this session wrote by hand in `claims-workflow-v2-poc/PRODUCTION-READINESS.md` — that document is, in effect, an unscored instance of this course's "production-readiness review" gate, organized by lens (AI agent / MCP / automation / regulatory) instead of by SLO metric.

The failure-analysis line "judge models can share the same blind spots as the system" is a sharper, more general version of a risk this session flagged narrowly for one POC: prompt injection via a free-text field that an LLM both reads *and* is asked to judge.

## Connects to

- [Concept: Decision Ledger pattern](../concepts/decision-ledger-pattern.md) — release gates and decision ledgers are both "don't let a probabilistic system's output become a fact without a recorded, versioned check first."
- [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.md)'s `PRODUCTION-READINESS.md` — a real, human-written instance of this course's gate, worth comparing against the course's own rubric to see what it's missing (it has no explicit release-gate *thresholds*, only qualitative gaps).

## Verified

ZH sibling ingested 2026-07-16: Python code byte-identical, heading count matches (7/7).

## Sources

`raw/courses/06-production-ai-engineering/README.md`
