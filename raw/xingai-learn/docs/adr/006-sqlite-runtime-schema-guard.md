# ADR-006: SQLite Runtime Schema Guard Before Alembic

**Date:** 2026-07-14  
**Status:** Accepted  
**Author:** Xing @ XingAI  
**Also available:** [中文](006-sqlite-runtime-schema-guard.zh.md)

## Context

Learn AI is still SQLite-first and does not yet have Alembic migrations. The real metadata cache work added new columns to existing local tables, especially `patterns` provenance fields. `Base.metadata.create_all()` creates missing tables but does not alter existing SQLite tables.

Without a guard, existing local databases fail during catalog import.

## Decision

Add a small SQLite-only runtime schema guard in `init_db()`:

1. For SQLite databases, inspect the existing `patterns` table.
2. Add missing provenance/cache columns required by the real-data importer.
3. Keep the guard narrow and temporary.
4. Do not use this pattern as a substitute for a real migration system once schema churn increases.

## Consequences

Positive:

- Existing local `learn.db` files continue to work after the real metadata cache upgrade.
- The importer can run without asking every developer to delete their local database.

Tradeoffs:

- This is not a full migration framework.
- It only handles known local SQLite columns.
- Future production persistence should move to Alembic or an equivalent migration workflow.

## Implementation

- `apps/api/app/database.py::ensure_sqlite_runtime_columns`

## Related

- ADR-004: Cache-Always Strategy for Real Learning Data
