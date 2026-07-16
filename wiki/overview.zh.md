# 总览

English: [overview.md](overview.md)

从这里开始。本 wiki 持续积累公开的 XingAI AI 工程学习资料:
[xingai-enterprise-ai-design](products/xingai-enterprise-ai-design.zh.md) 中的
基础课程与设计文档,
[xingai-enterprise-ai-pocs](https://github.com/xingaiapp/xingai-enterprise-ai-pocs)
中可运行(及仅设计)的 POC,
[xingai-engineering-system](products/xingai-engineering-system.zh.md) 中可复用
的模式,以及
[xingai-tech-blog](products/xingai-tech-blog.zh.md) 中精选的文章。

私有产品仓库不在范围内。完整目录见 [index.zh.md](index.zh.md)。

## 课程一句话概览

00 [基础](courses/00-ai-foundations.zh.md) → 01 [LLM 应用工程](courses/01-llm-application-engineering.zh.md) → (02 [RAG](courses/02-rag-knowledge-systems.zh.md) / 03 [工具调用与 Agent](courses/03-tool-use-ai-agents.zh.md)) → 04 [MCP](courses/04-mcp-interoperability.zh.md) → 05 [Agent 运行时与多 Agent](courses/05-agent-runtime-multi-agent.zh.md) → 06 [生产级 AI 工程](courses/06-production-ai-engineering.zh.md) → 07 [企业决策系统](courses/07-enterprise-decision-systems.zh.md) → 08 [AI 领导力与 CTO](courses/08-ai-leadership-cto.zh.md) → 09 [AI 面试精通](courses/09-ai-interview-mastery.zh.md)。

进阶延续课程(索引已快照,正文尚未完整摄入):
[deep-enterprise-ai](https://github.com/xingaiapp/xingai-enterprise-ai-design/tree/main/deep-enterprise-ai)。

## 贯穿全局的核心思想

1. **[5W+How](concepts/5w-how-framework.zh.md)** —— 每门课程的结构骨架。
2. **[决策台账(Decision Ledger)](concepts/decision-ledger-pattern.zh.md)** —— 第 07 课 + claims POC + engineering-system 的 schema。
3. **[缓存 / 兜底](concepts/cache-first-llm-architecture.zh.md)** —— 控制成本;绝不让单次 LLM 调用成为唯一路径。
4. **[Agent 治理与 MCP](concepts/agent-governance-and-mcp.zh.md)** —— 两道墙(scope 与 policy);oauth POC 对比 coverage POC。
5. **[Loop 工程](concepts/loop-engineering.zh.md)** —— 在文章、模式文档和 POC 中一以贯之的显式状态与停止条件。

## 本 wiki 新增了什么

`raw/` 是快照。`wiki/` 必须回答单份 README 回答不了的问题:

- Auth 优先 vs Coverage 优先 vs 工作流 —— [Claims POC 家族](syntheses/claims-poc-family-tradeoffs.zh.md)
- 第 04 课的"confused deputy"清单在哪里变成了 oauth 的第 1/2 道墙,又在哪里变成
  partner-api 的"auth 延后"
- 第 05 课关于 checkpoint 的告诫在哪里对应上 workflow-v2"每次调用重建图"的取舍
- 模式包命名(`decision-ledger-schema`)对比 POC 字段命名(`DecisionLedger`、
  SQLite trace)

如果一个页面只是缩短版 README 或文件列表,它就没通过 `AGENTS.md` 里的综合门槛
——需要重写。

## 日志

见 [log.md](log.md)(仅英文,运维日志例外)。
