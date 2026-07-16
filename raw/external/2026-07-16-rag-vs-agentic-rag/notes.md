# Notes — visual read (verified: partial)

Asset: `assets/rag-vs-agentic-rag.png`

## Title

**RAG vs Agentic RAG** — three panels (not two), despite the title.

## Panel A — RAG (top left)

Linear pipeline:

User → Query → **Retrieval** (Embedding ← Data Sources; Embedding → Vector Db) → **Augmented** (Retrieved Info + Query + System Prompt) → **Generation** (Large Language Model) → Output → User.

Data-source icons: document / image / video / audio.

## Panel B — AI Agent (top right)

Labeled under the Agentic umbrella in the title, but the box title is **AI Agent**:

User → Query → Agent (robot) with **Memory** + **Planning**; Agent ↔ **Tools** ↔ Data Sources; Agent → Output → User.

No explicit Vector Db / embedding path in this panel — retrieval is implied via Tools.

## Panel C — Multi-Agent RAG (bottom)

User → Query → **Aggregator Agent** with Memory (Short Term & Long Term) and Planning (ReAct & CoT).

Aggregator fans out to Agent 1 / Agent 2 / Agent 3, which talk to **MCP Servers**:

- Agent 1 → Local Data Servers → Local Data Sources
- Agent 2 → Search Engine (Kagi logo) → Cloud Servers
- Agent 3 → Cloud Engine (AWS + Azure logos) → Cloud Servers

Results return to Aggregator → Generative Model → Output → User.

## Authorship

No explicit author / company credit readable on the crop. Vendor logos (Kagi, AWS, Azure) are examples inside the Multi-Agent panel, not poster authorship.
