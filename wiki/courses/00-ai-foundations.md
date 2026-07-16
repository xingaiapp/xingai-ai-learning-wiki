# Course 00: AI Foundations

Chinese: [00-ai-foundations.zh.md](00-ai-foundations.zh.md)

**Prerequisite:** none · **Gate:** 80% · **Next:** [01 LLM Application Engineering](01-llm-application-engineering.md)

The entry point for the whole curriculum: explain AI/ML/deep learning/transformers/tokens/embeddings precisely enough to prevent "magical thinking" later, run a tiny semantic-similarity example (cosine distance over hand-supplied vectors), and — the load-bearing skill — identify where model output can fail (fluency mistaken for truth, one anecdote standing in for evaluation, benchmark scores mistaken for product outcomes).

The system-view diagram (`User → Tokenizer → Transformer → Decoder → Probabilistic output → Evaluation`) is the mental model every later course assumes: a model is a probabilistic component inside a larger product, not an oracle.

## Connects to

- [01 LLM Application Engineering](01-llm-application-engineering.md) — takes "the model is probabilistic" and turns it into "therefore validate its output with a schema."
- [Concept: 5W+How framework](../concepts/5w-how-framework.md) — this course is where the framework itself is first taught in miniature (What/Why/Who/When/Where/How as headers).
- [09 AI Interview Mastery](09-ai-interview-mastery.md) — the beginner interview track ("What is an embedding?") starts from exactly this course's vocabulary.
- External pedagogy aid: [Layers of AI vs curriculum](../syntheses/layers-of-ai-vs-curriculum.md) — street "Classical→Agentic" stack mapped onto this course path (and where the poster oversells autonomy).

## Verified

Code example checked by hand: `cosine([1,0],[1,0]) == 1.0` and `cosine([1,0],[0,1]) == 0.0` both correct. External sources ([Attention Is All You Need](https://arxiv.org/abs/1706.03762), [NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework)) resolve to real primary sources (checked 2026-07-16). ZH sibling ingested 2026-07-16: Python code block byte-identical, Mermaid diagram meaning matches (node labels translated, structure identical), heading count matches (9/9).

## Sources

`raw/courses/00-ai-foundations/README.md`; external stack graphic via `raw/external/2026-07-16-layers-of-ai/`
