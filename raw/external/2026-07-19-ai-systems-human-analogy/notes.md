# Notes — evaluate → fix → correct → draw

## Classification

- Third-party teaching poster by **Aiswarya Venkitesh**: body analogy for LLM / RAG / AI Agent / MCP.
- Frame image is title + follow CTA only; content is the four-row panel.
- Reference-only under `assets/*-reference.png`.

## Source evaluation (vs XingAI)

- **Source claim (1 line):** Think of AI like a human body — LLM=brain, RAG=brain+books, Agent=brain+hands, MCP=nervous system that connects everything / foundation layer.
- **Right (keep):**
  - LLM generates from learned patterns; RAG adds external docs/DBs; agents take actions with tools/memory; MCP is about connection to external capabilities.
  - Composition intuition (not only a naked LLM) is directionally useful for beginners.
- **Wrong (must fix):**
  - Error: **MCP = nervous system / foundation connecting everything** → Correction: MCP is **agent↔tool** protocol with **two walls**; not the foundation of LLM/RAG; peers may use A2A ([mcp-vs-a2a-vs-acp](../../wiki/syntheses/mcp-vs-a2a-vs-acp.md)).
  - Error: Four equal “organs” stacked as one body → Correction: **jobs/layers that compose**, not body parts; “vs” exclusivity fails ([mcp-vs-rag-vs-skills](../../wiki/syntheses/mcp-vs-rag-vs-skills.md)).
  - Error: LLM = “core intelligence” / The Brain → Correction: LLM is a **generator**; product intelligence needs retrieval governance, tool auth, loop stops, ledger.
  - Error: RAG = “brain + books” only → Correction: governed retrieval — ACL before ranking, citations, faithfulness eval ([Course 02](../../wiki/courses/02-rag-knowledge-systems.md)).
  - Error: Agent = “brain + hands” → Correction: Validate → Approve/Execute; durable loop + stop; not free hands ([Course 03](../../wiki/courses/03-tool-use-ai-agents.md), [loop-engineering](../../wiki/concepts/loop-engineering.md)).
- **Missing (add if needed):**
  - MCP two walls; A2A peer hop distinct from MCP.
  - Untrusted observations (RAG/tool text can steer agents).
  - Decision ledger / HITL for high-risk ACT.
- **Dangerous if followed as-is:**
  - Treating MCP as a universal “nervous system” and skipping auth.
  - Shipping agents that “take actions” without gates.
  - Believing RAG is safe because it “uses docs.”

## XingAI understanding map (post-fix)

- **Keep:** LLM / RAG / Agent / MCP as named jobs worth teaching.
- **Fixed claims (on PNG):** four **jobs** in a compose diagram (not body organs); MCP labeled tool-hop + walls; Agent labeled gated ACT; RAG labeled ACL+cite+eval; LLM labeled generator not “core intelligence.”
- **Drop:** purple/blue/orange body-row layout; brain/books/hands/nervous icons as architecture; author follow CTA; “human body” title.
- **Add:** “compose, don’t analogize organs”; Courses 02–05 footer; A2A footnote for peer hops.
- **Regroup:** 2×2 job cards around a center “One product system” OR horizontal job spine — **not** four stacked body metaphors.
- **One-glance claim:** *LLM generates · RAG retrieves under policy · Agent acts under gates · MCP is a tool hop with walls — not a human body.*
