# Notes — evaluate → fix → correct → draw

## Classification

- **Third-party poster:** ByteByteGo three-column MCP | A2A | ACP infographic.
- Ownership: **reference-only** under `assets/bytebytego-mcp-a2a-acp-reference.png`.
- Wiki embeds **XingAI-corrected** map only.

## Source evaluation (vs XingAI)

- **Source claim (1 line):** Three parallel protocols explain how agents talk — MCP to tools, A2A to agents via registry/cards, ACP to agents via REST/manifest.
- **Right (keep):**
  - MCP path host → client → server → structured tool results is directionally correct.
  - A2A peer discovery + delegation + “more information needed” loop matches high-level A2A task collaboration.
  - MCP and A2A solve different edges (tools vs peers) — complementary, not the same hop.
- **Wrong (must fix):**
  - Error: Title/framing **“vs”** + three equal columns → Correction: **MCP ∥ A2A** composition; one task can use both hops.
  - Error: **ACP as a third peer protocol** equal to A2A → Correction: ACP is **historical / merged into A2A** (footnote), not a live third column.
  - Error: MCP column ends at “pick server / external tools” with vendor stickers → Correction: MCP is a **governed capability boundary** (two walls: scope + business policy).
  - Error: A2A/ACP columns show happy-path discovery with no auth → Correction: peer hops need **trust / audience / allowlist**; Agent Card ≠ authorized tool call.
  - Error: No stop on *when* to add Agent B → Correction: Course 05 rule — add peers only for specialization, trust separation, or parallelism; block cyclic delegation.
- **Missing (add if needed):**
  - Review→Execute / ledger for high-impact side effects.
  - In-process multi-agent + MCP still valid without A2A on the wire.
  - Courses 04 / 05 / agent-governance links on the map footer.
- **Dangerous if followed as-is:**
  - Shipping “discover any Agent Card and delegate” without identity/policy.
  - Treating tool logos as architecture.
  - Implementing ACP as a parallel production stack beside A2A from the poster alone.

## XingAI understanding map (post-fix)

- **Keep (only after eval):** MCP = tool hop; A2A = peer hop; input-needed loop between agents; structured results.
- **Fixed claims (appear on PNG):**
  1. One user task → compose hops (not pick a column).
  2. Tool hop: Host → MCP Client → Server → **Wall 1 OAuth/scope** → **Wall 2 business policy** → tool result.
  3. Peer hop (optional): Agent Card discovery → auth/trust check → delegate → result or input-required; **no cyclic delegation**.
  4. ACP = lineage footnote under A2A (REST/async ideas absorbed), not column 3.
- **Drop:** Three equal columns; purple/blue/green protocol beauty contest; PostgreSQL/GitHub/Drive/Claude/Cursor stickers; ByteByteGo credit; “vs” as architecture.
- **Add (corrections):** Two-wall MCP; peer auth; Course 05 specialization gate; “not a protocol shopping list.”
- **Regroup:** Horizontal bands (Compose → Tool hop → Peer hop → Footnote) instead of three vertical protocol towers.
- **One-glance claim for NEW PNG:** *One task, two hop types — MCP for tools (with walls), A2A for peers (with trust); ACP is history under A2A.*

## Generate brief (for GenerateImage — no source reference)

See turn: landscape XingAI map from this understanding only.
