# Product family: xingai-enterprise-ai-design

Chinese: [xingai-enterprise-ai-design.zh.md](xingai-enterprise-ai-design.zh.md)

**Repo:** [xingai-enterprise-ai-design](https://github.com/xingaiapp/xingai-enterprise-ai-design)

Curriculum + design articles + labs. The wiki's course pages (`wiki/courses/`) are the **entity layer**; this page is how the *rest* of the design repo plugs into them.

## Layers (don't flatten them)

| Layer | Role | In this wiki |
|---|---|---|
| Foundation `courses/` 00–09 | Hireable AI-engineer path | Entity pages under `wiki/courses/` |
| `articles/` + `guides/` | Deep dives / labs that courses cite | Snapshotted under `raw/xingai-enterprise-ai-design/`; linked from concepts/POCs |
| `deep-enterprise-ai/` | Advanced continuation after foundation | Index only for now — don't pretend bodies are ingested |
| `assessments/` / capstones / interview-bank | Evidence gates | README snapshotted; not expanded into wiki entities yet |

## Boundary the index keeps repeating

This curriculum is **not** Learn AI (coding-pattern practice). Course 09 is AI-engineering interview loops. If a question is "two pointers vs sliding window," it does not belong here — see course index wording in `raw/courses/README.md`. This wiki does not ingest private Learn AI ADRs.

## How articles should be used

Prefer linking an article from a **concept or POC tension** (e.g. third-party MCP auth from [agent-governance](../concepts/agent-governance-and-mcp.md)) rather than creating one wiki page per article. Articles are already well-structured; duplication is pure loss.

## Connects to

- All [courses](../index.md#courses-wikicourses), [Claims POC family](../syntheses/claims-poc-family-tradeoffs.md)

## Sources

`raw/xingai-enterprise-ai-design/README.md`, `raw/courses/README.md`, articles/guides trees under `raw/xingai-enterprise-ai-design/`
