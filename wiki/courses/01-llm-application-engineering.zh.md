# 第 01 课:LLM 应用工程

English: [01-llm-application-engineering.md](01-llm-application-engineering.md)

**先修课程:** [00 AI 基础](00-ai-foundations.zh.md) · **通过门槛:** 带类型、有测试的应用 · **下一课:** [02](02-rag-knowledge-systems.zh.md)、[03](03-tool-use-ai-agents.zh.md)

从"理解模型"转向"用模型构建产品"的转折点:一个 LLM 应用就是围绕一个概率性
模型边界搭建的常规软件。承重的核心思想是把模型调用放在一个服务边界之后,并
用带类型的 schema(原始文档中的 `parse_triage`)校验输出,而不是相信自由文本
——这与 [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.zh.md) 用
启发式/LLM 双路径兜底所遵循的纪律完全相同。

从这里分出两门课程,而不是一门:02(RAG)和 03(工具调用/Agent)都假设了本
课程的带类型边界纪律,但朝不同方向延伸(检索 vs 行动)。

## 关联

- [概念:缓存 / 兜底 LLM 纪律](../concepts/cache-first-llm-architecture.zh.md)
  ——本课程"校验、窄范围重试、观测、安全降级"的清单,正是该概念中确定性软件
  的那一半。
- [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.zh.md)——在一个
  可运行的公开 POC 中,围绕模型调用的带类型/启发式边界。

## 关于来源的说明

原始来源引用了 `developers.openai.com/api/docs/guides/function-calling` 作为
OpenAI 函数调用的出处。这个域名看起来不太寻常(大多数 OpenAI 文档历史都在
`platform.openai.com`),但已于 2026-07-16 通过网络搜索核实为真实可解析的一手
来源——不是笔误。

ZH 版本于 2026-07-16 摄入:Python 代码块逐字节一致,标题数一致(7/7),
Mermaid 含义一致。

## 来源

`raw/courses/01-llm-application-engineering/README.md`
