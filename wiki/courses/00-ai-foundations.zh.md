# 第 00 课:AI 基础

English: [00-ai-foundations.md](00-ai-foundations.md)

**先修课程:** 无 · **通过门槛:** 80% · **下一课:** [01 LLM 应用工程](01-llm-application-engineering.zh.md)

整套课程体系的入口:精确解释 AI/ML/深度学习/Transformer/token/embedding,
使之足以在后面的课程中防止"魔法式思维",跑一个极小的语义相似度示例(在手工
提供的向量上做余弦距离),以及——这是承重的技能——识别模型输出可能在哪里
出错(把流畅误认为真实、用一个个案代替系统评测、把基准分数误认为产品结果)。

系统视图图示(`用户 → Tokenizer → Transformer → Decoder → 概率性输出 → 评测`)
是后续每门课程都默认成立的心智模型:模型是更大产品中的一个概率性组件,不是
神谕。

## 关联

- [01 LLM 应用工程](01-llm-application-engineering.zh.md)——把"模型是概率性的"
  这一点,转化为"因此要用 schema 校验它的输出"。
- [概念:5W+How 框架](../concepts/5w-how-framework.zh.md)——本课程是该框架本身
  首次以微缩形式被教授的地方(What/Why/Who/When/Where/How 作为标题)。
- [09 AI 面试精通](09-ai-interview-mastery.zh.md)——入门级面试题("什么是
  embedding?")正是从本课程的词汇体系开始的。

## 已验证

手工核对代码示例:`cosine([1,0],[1,0]) == 1.0`、`cosine([1,0],[0,1]) == 0.0`,
均正确。外部来源([Attention Is All You Need](https://arxiv.org/abs/1706.03762)、
[NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework))经核实
均为可解析的真实一手来源(核实于 2026-07-16)。ZH 版本于 2026-07-16 摄入:
Python 代码块逐字节一致,Mermaid 图示含义一致(节点标签已翻译,结构相同),
标题数一致(9/9)。

## 来源

`raw/courses/00-ai-foundations/README.md`
