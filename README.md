# pgsense

**PostgreSQL Index Intelligence**  
Safe, human-in-the-loop index analysis and recommendations for PostgreSQL.

`pgsense` is an open-source, Postgres-native tool that analyzes index usage, cost, and effectiveness, then generates **actionable, non-destructive recommendations**. It helps teams control index sprawl, prevent performance regressions, and reduce unnecessary write overhead — without automating risky schema changes.

---

## Why `pgsense` exists?

PostgreSQL provides strong observability but **no automated index lifecycle management**.

In practice this leads to:

- Unused indexes accumulating silently
- Missing indexes causing slow queries
- Excessive write amplification
- Index cleanup being postponed due to risk

`pgsense` provides **index intelligence**, not automation.

---

## Project Goals

`pgsense` aims to:

- Analyze index usage and operational cost
- Identify missing, redundant, or low-value indexes
- Support safe index cleanup workflows
- Generate explainable, confidence-scored recommendations
- Keep humans in full control

---

## Non-Goals

`pgsense` does **not**:

- Automatically create or drop indexes
- Replace DBAs or PostgreSQL’s query planner
- Modify PostgreSQL internals
- Require superuser privileges

---

## High-Level Architecture

```
Collector → Analyzer → Recommender → Reporter
```

### Collector

- Reads PostgreSQL system catalogs and statistics
- Uses standard views such as:
  - `pg_stat_user_indexes`
  - `pg_stat_statements`
  - `pg_class`, `pg_index`, `pg_attribute`

### Analyzer

- Applies heuristics to classify index value
- Uses time-windowed usage, size, and cost signals

### Recommender

- Produces **SQL recommendations only**
- Assigns confidence scores and reasoning
- Never executes changes

### Reporter

- Outputs results via:
  - CLI
  - JSON
  - Markdown
  - Optional Web UI

---

## Core Features (MVP)

### 1. Index Usage Classification

Indexes are classified as:

- **Actively used**
- **Rarely used**
- **Never used**

Based on scan counts, access patterns, and time windows.

---

### 2. Missing Index Detection

- Sequential scan analysis
- Frequent `WHERE` / `JOIN` patterns
- High-cost queries lacking index support

---

### 3. Index Cost & Bloat Analysis

- Index size vs real-world usage
- Write amplification impact
- Read/write trade-off evaluation

---

### 4. Safe Drop Candidate Workflow

Indexes move through a controlled lifecycle:

```
Mark → Observe → Recommend → Manual Drop
```

No automatic drops. No surprises.

---

## Safety Principles

- Read-only by default
- No automatic schema changes
- Human approval required
- Time-window based analysis
- Cloud-safe defaults

---

## Technology Stack

- **Language**: TypeScript
- **Database**: PostgreSQL
- **Interfaces**:
  - CLI (initial)
  - Web UI (optional)
- **Output Formats**:
  - SQL
  - JSON
  - Markdown

---

## Supabase & Managed PostgreSQL Support

Designed for managed and cloud environments:

- Works with pooled connections
- RLS-aware analysis
- No superuser access required
- Compatible with Supabase, RDS, Cloud SQL
- Conservative defaults for shared databases

---

## Project Status

Development is driven via GitHub Issues and Milestones.
Milestones reflect current priorities and may change as the project evolves.

## License

MIT
