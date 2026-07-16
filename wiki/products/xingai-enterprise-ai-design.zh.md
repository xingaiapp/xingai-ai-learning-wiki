# 产品族:xingai-enterprise-ai-design

English: [xingai-enterprise-ai-design.md](xingai-enterprise-ai-design.md)

**仓库:** [xingai-enterprise-ai-design](https://github.com/xingaiapp/xingai-enterprise-ai-design)

课程 + 设计文章 + labs。本 wiki 的课程页(`wiki/courses/`)是**实体层**;本页说明设计仓库*其余部分*如何接到它们上。

## 分层(不要压扁)

| 层 | 角色 | 在本 wiki 中 |
|---|---|---|
| 基础 `courses/` 00–09 | 可雇佣的 AI 工程师路径 | `wiki/courses/` 下的实体页 |
| `articles/` + `guides/` | 课程引用的深挖 / labs | 快照在 `raw/xingai-enterprise-ai-design/`;从概念/POC 链出 |
| `deep-enterprise-ai/` | 基础赛道之后的进阶延续 | 目前仅索引——不要假装正文已摄入 |
| `assessments/` / capstones / interview-bank | 证据闸门 | README 已快照;尚未展开成 wiki 实体 |

## 索引反复强调的边界

这套课程**不是** Learn AI(编码模式练习)。第 09 课是 AI 工程面试回路。若问题是「双指针 vs 滑动窗口」,就不属于这里——见 `raw/courses/README.md` 的课程索引措辞。本 wiki 不摄入私有 Learn AI ADR。

## 文章该怎么用

优先从**概念或 POC 张力**链到文章(例如从[agent 治理](../concepts/agent-governance-and-mcp.zh.md)链到第三方 MCP 鉴权),而不是一篇文章一页 wiki。文章本身已经结构良好;复制等于纯损失。

## 关联

- 全部[课程](../index.zh.md#课程wikicourses)、[Claims POC 族](../syntheses/claims-poc-family-tradeoffs.zh.md)

## 来源

`raw/xingai-enterprise-ai-design/README.md`, `raw/courses/README.md`, `raw/xingai-enterprise-ai-design/` 下的 articles/guides 树
