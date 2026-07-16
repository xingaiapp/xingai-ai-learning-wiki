# Product family: xingai-engineering-system

**Repo:** [xingai-engineering-system](https://github.com/xingaiapp/xingai-engineering-system)

Not a product. A pattern pack ("patterns, not libraries") that products copy into their own DBs and repos. For this wiki, the useful move is to see the **same idea** under three names:

| Pattern doc | Course / POC rhyme |
|---|---|
| `decision-ledger-schema` | Course 07 teaching `Decision` + workflow-v2 `DecisionLedger` |
| `worker-cache-boundary` / `cache-first-before-llm` | Course 01/06 cost discipline; workflow-v2 dual-path is the *fallback* cousin |
| `loop-engineering-three-layer` / `micro-loop-engine` | [Loop engineering](../concepts/loop-engineering.md) articles + ADR-005 |
| `agent-execution-gate` + ADR-002 | Course 03 approve/execute; oauth POC walls |

## What not to do

Do not paste the schema markdown into every product page. Link here, then say how a *specific* POC conforms or diverges (e.g. workflow-v2 pins `model_version` but still lacks model change-management process — named in its PRODUCTION-READINESS).

## Connects to

- [Concept: Decision Ledger pattern](../concepts/decision-ledger-pattern.md), [Concept: Cache / fallback](../concepts/cache-first-llm-architecture.md), [Concept: Loop engineering](../concepts/loop-engineering.md)

## Sources

`raw/xingai-engineering-system/patterns/*` (selected), `raw/xingai-engineering-system/docs/adr/002-agent-execution-safety.md`
