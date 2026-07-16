# Synthesis: Courses vs. xingai-learn — Not Duplicates

**Question that prompted this page:** "there are 2 learn course in this workspace" (2026-07-16) — are `xingai-enterprise-ai-design/courses/` and `xingai-learn` the same thing twice?

**Answer: no.** They share the word "learn"/"course" and both touch "interview prep," but serve different domains:

| | `courses/` | `xingai-learn` |
|---|---|---|
| Type | Written bilingual curriculum (10 courses, `.md`/`.zh.md` peers) | Live product (learn.xingai.app, Next.js + FastAPI + SQLite) |
| Content | AI engineering, foundations → CTO strategy | General coding-interview pattern practice (187 patterns, 16 families) |
| Consumed by | A human reading/studying | A user pasting a LeetCode-style question for analysis |
| Relationship to interviews | [Course 09](../courses/09-ai-interview-mastery.md) is about *AI-engineering-specific* interview loops (ML depth, AI system design, agent/RAG/MCP tradeoffs) | Practices *general* DS&A patterns (two pointers, sliding window, DP) — not AI-specific at all |

The one real overlap is conceptual, not content: both are "interview prep," and Course 09's tracks assume the vocabulary Courses 00-08 teach, while xingai-learn assumes a completely different (classic CS) knowledge base. Confirmed by reading both `xingai-learn/README.md`'s MVP feature list (Question Classification, Pattern Engine + Knowledge Graph, Company Mode) and `xingai-learn/docs/adr/001-product-boundary.md`'s own explicit boundary-setting against Research AI and SAT AI — xingai-learn's own ADR-001 is already doing this exact kind of boundary discipline, just against different sibling products than Course 09.

## Verdict

No consolidation needed. If anything, the useful next step (not done as part of this trial) would be a cross-link *from* `xingai-learn/docs/adr/001-product-boundary.md` *to* Course 09 — that ADR currently draws its boundary against Research AI and SAT AI but doesn't mention the courses curriculum at all, even though "AI Interview Mastery" is the course most likely to be confused with it.

## Sources

Chat analysis, 2026-07-16 (this session) — not derived from a single raw file; cites `raw/xingai-learn/README.md` and `raw/xingai-learn/docs/adr/001-product-boundary.md` and `raw/courses/09-ai-interview-mastery.md`.
