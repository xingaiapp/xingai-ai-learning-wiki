# XingAI AI 学习 Wiki

English: [README.md](README.md)

Andrej Karpathy [LLM Wiki 模式](raw/_llm-wiki-pattern.md)的一次试运行：
不是每次提问都从原始文档重新推导答案，而是由 LLM agent 持续构建、维护一份
可持久积累、互相交叉引用的 wiki。

**范围：** 公开的 XingAI AI 工程学习资料 —— 课程与设计文档来自
[`xingai-enterprise-ai-design`](https://github.com/xingaiapp/xingai-enterprise-ai-design)，
POC 来自
[`xingai-enterprise-ai-pocs`](https://github.com/xingaiapp/xingai-enterprise-ai-pocs)，
模式文档来自
[`xingai-engineering-system`](https://github.com/xingaiapp/xingai-engineering-system)，
并精选部分
[`xingai-tech-blog`](https://github.com/xingaiapp/xingai-tech-blog) 文章。

`raw/` 存放快照。`wiki/` 是知识库：**已知 / 缺失 / 再思考 / 待辩论 / 需要更多证据**
—— 是综合与批判性分析,不是缩短版 README,也不是猜测。内容页均为**双语**
(`name.md` + `name.zh.md`)。详见 `AGENTS.md`。


## 仅限公开来源规则

本仓库是公开的。**不得**摄入、复制或摘要私有 XingAI 仓库的内容。优先使用绝对
GitHub 链接而非本地相邻路径。任何新的摄入前,先用 `gh` 确认可见性。

## 目录结构

```
raw/
  courses/                         基础课程 00–09(文件夹 README)
  xingai-enterprise-ai-design/     文章、指南、评估、深度企业 AI 索引
  pocs/                            所有公开 POC + docs/adr 001–009
  xingai-engineering-system/       精选模式文档 + ADR-002
  xingai-tech-blog/posts/          精选架构类文章
  _llm-wiki-pattern.md
wiki/                              LLM 撰写的目录(见 wiki/index.md)
AGENTS.md                          摄入 / 查询 / 检查的 schema
```

## 如何使用

先打开 `wiki/index.md`。让任何 LLM agent 以 `AGENTS.md` 作为 schema 来操作本仓库。

**Cursor 全局技能：**

- `xingai-ai-learning-wiki` —— 扫描/同步公开的 `xingaiapp` GitHub 仓库
- `xingai-wiki-ingest` —— 将 **URL / 图片 / 粘贴内容 / 本地文件** 摄入
  `raw/external/`,再更新 `wiki/`(是综合,不是复制粘贴)

用这些名字或 `/xingai-ai-learning-wiki`、`/xingai-wiki-ingest` 触发。

## 状态

试运行 / v0。最近一次全量公开仓库同步于 **2026-07-16**。wiki 内容页双语
(`wiki/**/*.md` + `*.zh.md`)。同日已删除第三方署名图片 wiki(Michael Lee /
Rishi 海报)——保留 XingAI 公开来源,以及仍有用的未署名批判包。需要时 UX PNG
放在 `wiki/assets/ux/`。最新外部摄入:RAG vs Agentic RAG 批判。跳过项:
`xingai-ai-learning-wiki`(自身)、`xingai-dot-app`(P2 营销站点)。深度企业课程
正文尚未完整快照(仅索引)。

## 免责声明

仅供教育/参考之用。详见 [DISCLAIMER.zh.md](DISCLAIMER.zh.md)。wiki 页面可能有误;
原始快照可能已过时。XingAI 不作任何担保。
