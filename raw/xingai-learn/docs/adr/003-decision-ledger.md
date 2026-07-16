# ADR-003: Decision Ledger Adoption

**Date:** 2026-07-05
**Status:** Accepted (implemented 2026-07-14)
**Author:** Xing @ XingAI
**Also available:** [中文](003-decision-ledger.zh.md)

## Context

Learn AI's README claims "Decision > Information" — the product's output is a recommendation the user acts on: *practice this pattern next*, *your readiness for Google is X*. The shared XingAI pattern for exactly this shape is the Decision Ledger (`xingai-engineering-system/patterns/decision-ledger-schema.md`), already adopted by invest-decision-engine (ADR-015/016), research-startup-agent (ADR-003), meal-coach-ai (ADR-003), and agent-firewall (ADR-003).

Today Learn AI stores rich domain tables (`LearningHistory`, `PatternMastery`, `ReadinessSnapshot`) but no `Decision` rows — so "did the user follow the recommendation, and did it help?" is answerable only by joining domain tables with per-product knowledge. The adoption checklist in the pattern explicitly requires each product to document its `domain` values and confidence semantics in its own ADR. This is that ADR.

## Decision

**Adopt the shared Decision schema unchanged, as a new table in the existing SQLite database.** One row is written when a recommendation is *shown to the user*, at these three points:

| `domain` | Written when | `recommendation` contains |
|---|---|---|
| `next-question` | Recommendation Engine returns the next question/pattern (end of `run_decision_pipeline`) | the recommended pattern slug + question title |
| `readiness` | a `ReadinessSnapshot` is computed and displayed | overall score + weakest area summary |
| `company-mode` | company-aware reweighting changes the recommendation vs. general mode | the company slug + what changed |

**Confidence semantics (per the pattern's calibration rule):** confidence is the Recommendation Engine's coverage-based certainty — how much of the user's history supports this recommendation (0.2 = fewer than 3 analyzed questions in this category; scales with `PatternMastery.attempts`). It is *not* comparable to Invest AI's confidence or the firewall's risk score.

**`action_taken` signal:** Learn AI actually has one, unlike most siblings — if the user analyzes/solves a question matching the recommended pattern within 7 days, mark `followed`; a different pattern, `modified`; nothing, leave null. `outcome` fills from the next `PatternMastery` update on that slug.

`source_ref` points at the product's own richer record: `learning_history.id` or `readiness_snapshots.id`.

## Consequences

Positive:
- "How many recommendations did I follow this month, and did mastery improve after?" becomes one query — this is the Interview Readiness story told with evidence.
- Learn AI becomes the fifth adopter; any future cross-product decision-history surface picks it up for free.

Tradeoffs:
- One extra write per analyze/readiness call (negligible next to the LLM call).
- The 7-day follow window is a heuristic and will misattribute some `followed` marks. Acceptable: the ledger is directional feedback, not billing.

## Implementation Status

Implemented 2026-07-14. Adoption checklist (from the shared pattern):

- [x] Add `Decision` table to `apps/api/app/models.py` matching the shared shape, plus one documented addition: `user_id` (the shared shape assumes a single-user product; Learn AI needs it to scope the 7-day matcher per user)
- [x] Write rows at the three points above — `next-question` and `company-mode` in `engines/decision.py::build_analyze_response`, `readiness` in `engines/readiness.py::compute_readiness`. New shared module: `app/decision_ledger.py`
- [x] Backfill `action_taken` via the 7-day matcher — `decision_ledger.backfill_action_taken`, called from `run_decision_pipeline` (new analysis) and `routers/questions.py::mark_solved`. Only judges the single most recent pending decision per action, per user, within its own 7-day window — older unresolved recommendations are left null rather than retroactively marked
- [x] Document actual confidence calibration — see below (implemented, not yet validated against real usage data since this just shipped)

### Confidence calibration (as implemented)

`next-question` / `company-mode`: `coverage_confidence()` in `decision_ledger.py` — 0.2 floor when the user has fewer than 3 analyzed questions in that `main_category`; otherwise `min(1.0, 0.3 + 0.1 * PatternMastery.attempts)` on the recommended pattern. `readiness`: `pattern_coverage / 100` from the same snapshot — how much of the full pattern catalog the number is actually grounded in, not a copy of `overall_score`. Both are placeholder-shaped, deliberately simple curves; the ADR's own two anchor points (0.2 floor, scales with attempts) are satisfied, but the exact slope has no real-usage data behind it yet. Revisit once there's enough `action_taken` history to check whether higher recorded confidence actually correlates with more `followed` outcomes.

## Related

- [ADR-001: Product Boundary](./001-product-boundary.md)
- [ADR-002: One LLM Call, Many Engines](./002-single-call-engines.md)
- xingai-engineering-system: `patterns/decision-ledger-schema.md`
