# XingAI Content Pack — Full Analysis

**Date:** 2026-07-16
**Engine:** manual (Claude, grounded in repo code)
**Issue:** Agent Adoption's Bottleneck Just Moved From Capability to Certification
**Featured opportunity:** Agent Skill Assurance & Evaluation
**Project Pick:** Agent Skill Assurance & Evaluation → Agent Firewall module

> Attached per ADR-006 §2 — this is the long-form payload the email body (ADR-006 §1) intentionally leaves out.

---

## Deep Analysis

**What changed:** Three signals landed the same week, each independently confirmed against a primary source: Anthropic's Claude for Teachers (July 14) extends agentic workflows to a second education buyer; Claude Sonnet 5 shipped cheaper long-task/computer-use pricing ($2/$10 per million input/output tokens through Aug 31, 2026, moving to $3/$15 after); NVIDIA published a Secure Agent Workspace reference design specifically for governing network/tool access on long-running agents. None of these are about a model getting smarter — all three are about the infrastructure required once an agent is trusted to run longer, touch more third-party tools, and get delegated more real, unsupervised work.

**Why it matters beyond this week:** The bottleneck in agent adoption has already shifted once, from "can it produce a good answer" to "can you trust what it did while you weren't looking" (the same insight behind Firewall's original build). This week's signals show the next turn of that same wheel: it's not enough to govern what an agent does at runtime if nobody certified the Skill/tool it's calling before that call ever happened. XingAI already has the runtime half of this story built (`xingai-agent-firewall`); the pre-production half is the gap this pick closes.

**Second-order effects:**
- If Skill Assurance ships as a Firewall module, every future governance-adjacent bet (fairness re-audits, model change-management gates — both flagged this week in `claims-workflow-v2-poc`'s own `PRODUCTION-READINESS.md`) should route through the same ledger/dashboard, not spawn parallel governance surfaces.
- The eval harness built here (sandbox → normal/edge/adversarial test cases → compare → decision) is the same primitive Research Experiment OS (this issue's #2 opportunity) needs — worth extracting as a shared component if both get built.
- Competitive response from other agent-governance vendors is likely to be feature-matching (add a permissions tab) rather than category-defining; XingAI's edge is that Firewall already has a working runtime enforcement story to attach certification to, not a certification tool bolted onto nothing.

**Risks:**
- Execution risk: the sandbox needs to run untrusted third-party code safely (network/file/shell isolation) — this is a materially bigger build than Firewall's existing policy-engine work, and the 2-week box is tight for a genuinely isolated multi-case, multi-model eval runner. Descope to one model provider and file-based Skills only (no live network calls in the eval cases) for the first 2 weeks if needed.
- Fit risk: confirm with a human founder decision that Firewall's existing dashboard/ledger can actually absorb a "Skills" concept without a schema migration that breaks existing Decision rows — check `engine/ledger.py`'s current schema before starting.
- Source risk: this issue's raw input referenced "Microsoft Memora," Meta "Muse Spark 1.1," and Google Research "Personal Health Agent" — none resolved to a verifiable primary source in this pass. The core thesis here does not depend on any of the three (it rests on Claude for Teachers, Sonnet 5 pricing, Claude Tag, and NVIDIA's two agent-governance/eval publications, all verified), but don't cite the unverified three in any published version of this issue.

## Architecture Recommendation

**Target repo:** `xingai-agent-firewall`
**Mode:** upgrade

**Components:**
- New `skills/` module alongside the existing `engine/` (policy.py, engine.py, ledger.py, notify.py, cli.py): `skills/importer.py` (parses SKILL.md / MCP manifest / repo into a `Skill` + `SkillVersion` record), `skills/capability_extractor.py` (static scan for network/file/shell/secrets/API requests, produces a `PermissionManifest`), `skills/eval_runner.py` (runs `EvaluationCase`s in an isolated sandbox, reusing whatever process/container isolation the existing policy engine already assumes for safety), `skills/scoring.py` (produces a `RiskScore` and a `ReleaseDecision`).
- Reuse `engine/ledger.py`'s existing Decision-row schema for every `ReleaseDecision` instead of a new table — a Skill certification is still fundamentally "what did we decide about an agent-adjacent action, and why."
- Dashboard: extend the existing Next.js/Shadcn dashboard with a `Skills` route reading from the same API the `Queue`/`Audit` views already use, not a separate frontend app.
- FastAPI: a `/skills/import`, `/skills/{id}/evaluate`, `/skills/{id}/versions` set of endpoints in the existing policy-engine API surface, following the same synchronous-verdict, local-first pattern as `/check`.

**Data flow:**
- 1. A Skill/MCP manifest is imported (CLI or dashboard upload).
- 2. `capability_extractor.py` produces a permission manifest; a human or policy rule flags anything requesting network/shell/secrets for closer review.
- 3. `eval_runner.py` runs the case set (start with a hand-written 20-case set per Skill, matching this week's "Build This Week" scope) inside the same isolation boundary Firewall's runtime hook already assumes exists.
- 4. `scoring.py` writes one `ReleaseDecision` as a Decision row in the existing ledger; the dashboard's new Skills tab reads it back.
- 5. Version-over-version comparison is a query over the ledger for the same `Skill` id, not a new mechanism.

**Integration points:**
- Reuse `config/portfolio.yaml`'s existing `agent-firewall` product id — no new portfolio entry needed since this is explicitly an upgrade, not a new product.
- Share the risk-scoring vocabulary already established in ADR-002 (deterministic rules first, LLM advisory only) rather than inventing a second scoring philosophy for Skills.
- If Research Experiment OS gets built later, its sandbox/eval-run primitive should import from `skills/eval_runner.py` rather than reimplementing sandboxed execution a second time in a different repo.

**XingAI standard principles applied:**
- Worker/engine owns all decision logic; FastAPI reads/writes through it, never recomputes a verdict in a request handler.
- i18n: every new dashboard string via `tr(lang, en, zh?, ko?)` with the typed Lang union, matching the rest of the Firewall dashboard.
- Theme: CSS variable classes only (`bg-background`, `text-foreground`, `border-border`, `bg-card`) — no new hardcoded colors for the Skills tab.
- SEO/AEO: not applicable — this is an internal/enterprise dashboard surface, not a public marketing page.
- Mobile-first layout, 44px touch targets, `overflow-x-auto` on the new Skills comparison table.

## Cursor Prompt

```
You are extending the existing XingAI Agent Firewall repo (xingai-agent-firewall)
with a new Skill Assurance & Evaluation module. Do NOT scaffold a new repo —
this is an upgrade of an existing product.

Context: xingai-agent-firewall already has engine/policy.py, engine/engine.py,
engine/ledger.py, engine/notify.py implementing policy check -> risk score ->
approval -> ledger for live agent tool calls (see docs/adr/001-003). This task
adds a pre-production counterpart: certifying a Skill/MCP tool BEFORE it's
ever called live.

MVP scope (2 weeks, do not exceed):
1. skills/importer.py — parse a SKILL.md file, an MCP server manifest (JSON),
   or a GitHub repo URL into a Skill + SkillVersion record: source, author,
   repository, commit SHA, license, version, owner, update date.
2. skills/capability_extractor.py — static-scan the imported content for
   requested capabilities: network, files, shell, browser, email, calendar,
   database, secrets, external APIs. Output a PermissionManifest.
3. skills/eval_runner.py — accept a small EvaluationDataset (input, expected
   behavior, forbidden behavior, available tools, success criteria, risk
   criteria) and run each EvaluationCase in an isolated sandbox (reuse
   whatever isolation the existing engine/ assumes; do not build a second,
   incompatible sandbox). Record: success, latency, token cost, tool calls,
   permission violations, unsafe actions, retries, failures.
4. skills/scoring.py — classify failures into: instruction failure, reasoning
   failure, retrieval failure, tool misuse, policy violation, timeout,
   excessive cost, regression. Produce a RiskScore and a ReleaseDecision:
   approved, approved-with-restrictions, testing-only, blocked, deprecated,
   rolled-back.
5. Write every ReleaseDecision as a Decision row into the EXISTING ledger
   schema in engine/ledger.py — do not create a parallel ledger table.
6. Add FastAPI endpoints: POST /skills/import, POST /skills/{id}/evaluate,
   GET /skills/{id}/versions, GET /skills/{id}/decisions — following the
   same synchronous-verdict pattern as the existing /check endpoint.
7. Add a Skills tab to the existing Next.js/Shadcn dashboard, next to the
   existing Queue and Audit tabs, reading from the new endpoints.
8. Support comparing two SkillVersions (regression diff) and, if more than
   one model provider is configured, comparing the same Skill across
   providers.

Follow the XingAI global standard exactly:
1. engine/ owns all decision logic; FastAPI reads/writes through it, never
   recomputes a verdict in a request handler.
2. Every new dashboard string goes through tr(lang, en, zh?, ko?) with a
   typed Lang union. No hardcoded English strings in JSX.
3. Theme via CSS variable classes only: bg-background, text-foreground,
   border-border, bg-card. No hex colors, no hardcoded Tailwind color classes.
4. Mobile-first layout, 44px minimum touch targets, overflow-x-auto on the
   new Skills comparison table.
5. This is an internal/enterprise dashboard surface — skip SEO metadata/AEO
   JSON-LD, they don't apply here.

Do NOT build (portfolio-wide guardrails from config/portfolio.yaml):
- A new repo or a parallel Decision ledger schema — everything above must
  land inside xingai-agent-firewall and its existing ledger.
- A standalone paid SKU for this at v1 — bundle into the existing
  Team/Enterprise tier.
- Live network calls inside adversarial eval cases without explicit sandbox
  isolation guarantees — this is exactly the kind of untrusted-code-execution
  risk the parent Firewall product exists to prevent.

Include: database migrations for the new tables/columns, 2-3 seed Skills with
seed evaluation cases, unit and integration tests (including a test that a
regressed version is correctly blocked), input validation, error handling,
and a README section describing the new module.
```

## PRD Draft

**Problem:** `xingai-agent-firewall` governs what an agent is allowed to do at runtime (policy → risk → approval → ledger per tool call), but has no way to certify a Skill or MCP tool *before* it's ever called live: no permission extraction, no regression testing across versions, no cross-model comparison, no formal approve/restrict/block release decision.

**Users:** AI Platform Team members standardizing which third-party Skills/MCP servers enter production; Agent Builders shipping their own Skills who need a pre-release regression gate; Security Engineers who already own Firewall's approval queue and need its pre-production counterpart.

**Goals:**
- Ship a working Skill import → permission extraction → sandboxed eval → release-decision pipeline inside the existing Firewall repo, reusing its ledger and dashboard.
- Prove the pattern with 2-3 real Skills and real regression detection (a deliberately broken v2 of a seed Skill should be correctly flagged) before committing further engineering.

**Non-goals:**
- A standalone product or repo — this explicitly extends Firewall, not a new SKU.
- Full multi-model comparison at v1 — start with one provider, add cross-model comparison once the single-provider path works.
- Live-network adversarial test cases at v1 — file/prompt-based adversarial cases only until sandbox isolation for network calls is verified safe.

**User stories:**
- As an AI Platform Team member, I want to import a third-party Skill and see its requested permissions and eval results before allowing it into a production agent stack, so that I can approve, restrict, or block it with evidence instead of guessing.
- As an Agent Builder, I want a regression gate on my own Skill's releases, so that a bad update to my Skill's prompt or logic is caught before it reaches a live session.
- As a Security Engineer, I want the same ledger my Firewall approval queue already writes to, so that runtime enforcement and pre-production certification show up in one unified audit trail, not two.

**Success metrics:**
- Import a real Skill and get a permission manifest + risk score in under 5 minutes.
- Correctly flag a deliberately regressed seed-Skill version as `blocked` or `approved-with-restrictions`, not `approved`.
- Generate a clear release recommendation (not just raw metrics) a human can act on without re-reading every test case.
- At least one internal Skill (from XingAI's own portfolio, e.g. a claims-workflow-v2-poc-style MCP tool) is actually run through the pipeline end-to-end as a real dry run, not just seed fixtures.

**2-week scope:** Skill/MCP manifest import, capability/permission extraction, a hand-written 20-case eval dataset run in an isolated sandbox, risk scoring + release decision written to the existing Firewall ledger, and a new Skills dashboard tab.

**Risks:**
- Sandbox isolation for untrusted Skill code is a materially bigger engineering lift than the rest of Firewall's existing (deterministic, no-code-execution) policy engine — budget accordingly and descope the isolation guarantees explicitly rather than silently under-building them.
- Ledger schema migration risk — verify `engine/ledger.py`'s current schema can absorb a `ReleaseDecision` row type without breaking existing Decision rows from the runtime-enforcement path.

## References

- [Introducing Claude for Teachers](https://www.anthropic.com/news/claude-for-teachers) — Anthropic
- [Introducing Claude Sonnet 5](https://www.anthropic.com/news/claude-sonnet-5) — Anthropic
- [Claude Platform pricing](https://platform.claude.com/docs/en/about-claude/pricing) — Anthropic
- [Introducing Claude Tag](https://www.anthropic.com/news/introducing-claude-tag) — Anthropic
- [Secure Agent Workspace Reference Design](https://docs.nvidia.com/enterprise-reference-architectures/secure-agent-workspace-reference-design/latest/index.html) — NVIDIA
- [Accelerating Federated Learning Research with AI Agents and NVIDIA FLARE Auto-FL](https://developer.nvidia.com/blog/accelerating-federated-learning-research-with-ai-agents-and-nvidia-flare-auto-fl/) — NVIDIA
- `xingai-agent-firewall/docs/PRD.md`, ADR-001 through ADR-006 — the existing product this pick upgrades
- `xingai-enterprise-ai-pocs/pocs/claims-workflow-v2-poc/PRODUCTION-READINESS.md` — the manual, human-run version of the exact evaluation this opportunity would automate; cited in this issue as working proof of the pattern
- **NEEDS MANUAL REVIEW:** "Microsoft Memora," Meta "Muse Spark 1.1," Google Research "Personal Health Agent" — present in the original raw report, not resolved to a verifiable primary source in this pass; do not cite in a published version without independent verification

_Not investment advice. Internal build-decision aid for XingAI founders only._
