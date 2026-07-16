# Visual notes — MCP vs RAG vs Skills

## Title

“MCP vs RAG vs Skills: Understanding architectures that improve AI agents.” Three columns: MCP (green), RAG (blue), Agent Skills (purple).

## MCP column (partial)

User Query → Server Application Request → MCP Host (MCP Client + LLMs; “Choose the right server”; Data from tools + Query → LLMs) ↔ MCP Server (Slack / Drant? / Brave Search) → Result to User. Client shows brand-like icons (e.g. Anthropic/GitHub/Brave-style marks — exact brands ambiguous).

## RAG column (partial)

Data Sources → Embedding (“dense numerical vector”) → Vector DB; User Query → Extract Data; Augmented = Retrieved Info + Query + System Prompt → Generative Model → Output to User.

## Agent Skills column (partial)

User Query → Agent Host (“Loads Skills”: Initializes actions / Selects tools / Performs actions) → LLMs ↔ Skill Manager (Skill Selection Add/Retrieve; Skill Request/Data) → Tools (File system, Git, Python Interpreter, Shell, Docker) → Code generation (SKILL.md) → Prompting / Actions → Final Output.

## Ambiguities

- “vs” in the title implies mutually exclusive choices; diagrams do not show composition (RAG *inside* MCP tools, Skills *orchestrating* both).
- MCP column has no OAuth / scopes / resource indicators.
- RAG column has no ACL-before-rank or citation/eval boxes.
- Skills column mixes runtime tools (Shell, Docker) with “SKILL.md” authoring artifact — same word, different layers (see XingAI blog Known).
- “Drant” likely Qdrant; not verified.
