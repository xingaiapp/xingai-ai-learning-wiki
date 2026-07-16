# 综合:「Layers of AI」vs XingAI 课程体系

English: [layers-of-ai-vs-curriculum.md](layers-of-ai-vs-curriculum.md)

流行信息图(用户于 2026-07-16 摄入):六个叠放圆柱——Classical AI → Machine Learning → Neural Networks → Deep Learning → Generative AI → Agentic AI。

资产:`raw/external/2026-07-16-layers-of-ai/`。

## 已验证(Known)

- 图上标签(视觉读,`verified: partial`):Classical(Symbolic / Expert Systems / Knowledge Representation / Logic & Reasoning);ML(Supervised / Unsupervised / Classification / RL / Regression);NN(Perceptrons / Cost / Backprop / Activations / Hidden Layers);DL(Transformers / LSTM / RNN / CNN / Autoencoders);GenAI(LLMs / Diffusion / Multimodal / VAE);Agentic(Memory / Planning / Tool Use / Autonomous Execution)。图上署名:「Follow Michael - From Pilots to Platforms。」
- XingAI 基础课程公开从第 00 课起讲词汇,深度主要落在 GenAI 应用边界到受治理 agent(第 01–05 课),外加生产/决策/CTO(06–08)——见 `raw/courses/README.md` 与课程实体页。
- 公开 claims POC 把延后鉴权、生产缺口、双墙鉴权写成*分开*的实验——不是「爬上紫色环就完事」([claims-poc-family-tradeoffs](claims-poc-family-tradeoffs.zh.md))。

## 缺失(海报上)

- 鉴权、评测、human-in-the-loop、决策台账、成本/运维——顶环一个都没有。
- 失败模式(提示注入、confused deputy、过时 checkpoint)。
- 「层」的任何引用或定义(历史?依赖?营销?)。

## 再想(Rethink)

- **叠层 ≠ 依赖。** Classical 规则与 ML 分类器仍坐在「agentic」POC 里(状态机、启发式回退)。把下层当成过时,是误读企业系统。
- **高度 ≠ 就绪。** 没有 OAuth/策略/台账的工具调用 demo,按 POC PRODUCTION-READINESS 文档仍是 demo。
- **Transformers vs LLMs** 拆在 DL 与 GenAI 环——重叠类别,不是干净地层。

## 辩论(留开)

- 「Agentic AI」是**能力层**(海报)还是**控制体制**(第 03–04 课 + MCP POC)?XingAI 材料偏向控制体制;海报不论证。
- Classical AI 应作为一等课程带教,还是只作为嵌入式策略?课程目前嵌入;海报把它抬成第 1 环。没有 ADR 裁定「加一门 Classical 课」。

## 需要证据

- 本图的规范 URL / 作者页(包内没有)。
- 是否有任何 XingAI 公开课程明确背书这套六环分类法(快照课程索引中未找到;缺席 ≠ 反证——若以后需要,可对设计仓库做全文检索)。

## 何时用

入门词汇与第 09 课面试探针(「治理放哪?」)。不要当 POC 架构图。

## 来源

`raw/external/2026-07-16-layers-of-ai/`(SOURCE.md、notes.md、assets/layers-of-ai.png); `raw/courses/README.md`; claims POC 族综合。视觉标签:`verified: partial`。
