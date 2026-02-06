# Contributing to pgsense

First off — thanks for considering contributing to **pgsense**.  
This project values **clarity, safety, and engineering judgment** over cleverness or automation.

If you’re here to improve PostgreSQL index intelligence responsibly, you’re in the right place.

---

## Core Philosophy

Before contributing, align with these principles:

- **Safety first**: No automatic or destructive actions
- **Read-only by default**: Analysis over mutation
- **Explainability**: Every recommendation must be justifiable
- **Human-in-the-loop**: Humans make final decisions, not the tool
- **Postgres-native**: Work with PostgreSQL, not against it

If a change violates these, it won’t be merged.

---

## Ways to Contribute

You can contribute in several ways:

- Reporting bugs or incorrect recommendations
- Improving heuristics and analysis accuracy
- Adding support for more PostgreSQL versions
- Improving documentation or examples
- Enhancing CLI UX or output formats
- Adding tests, benchmarks, or edge-case coverage

Low-effort or speculative features without clear value will be rejected.

---

## Development Setup

### Prerequisites

- PostgreSQL 15+
- Bun
- Access to a test database with realistic data
- `pg_stat_statements` enabled

---

## Project Structure (Expected)

```
TODO: YET TO ARRIVE
```

Keep concerns separated. No god-packages.

---

## Heuristics & Analysis Rules

When adding or modifying heuristics:

- Document **why** the heuristic exists
- Explain false positives and false negatives
- Prefer conservative recommendations
- Avoid hard-coded thresholds without justification
- Support time-window based analysis

Every heuristic should be explainable to a DBA.

---

## Recommendations & Output

All recommendations must:

- Be **non-destructive**
- Include reasoning and confidence scores
- Output SQL without executing it
- Be deterministic and reproducible

If a recommendation cannot be explained, it does not belong in `pgsense`.

---

## Testing Guidelines

- Add unit tests for all analysis logic
- Use fixtures based on real Postgres catalog data
- Test against multiple Postgres versions where possible
- Include negative tests (ensure unsafe actions are not suggested)

Untested heuristics will not be accepted.

---

## Pull Request Guidelines

Before opening a PR:

- Ensure tests pass
- Update or add documentation if behavior changes
- Keep PRs focused and small
- Avoid drive-by refactors

PRs should answer:

- What problem does this solve?
- Why is this safe?
- How does this affect existing recommendations?

---

## Coding Standards

- Prefer readability over cleverness
- Be explicit rather than implicit
- Avoid magic numbers
- Log decisions, not just outcomes
- Fail loudly and clearly

This is infrastructure tooling — correctness matters more than style.

---

## Backward Compatibility

- Do not break output formats without discussion
- Heuristic changes must be noted as behavior changes
- CLI flags should be stable and predictable

Breaking changes require justification.

---

## Issue Reporting

When filing an issue, include:

- PostgreSQL version
- Dataset size (approximate)
- Relevant indexes and queries
- Output produced by `pgsense`
- Why the output is incorrect or risky

Issues without context will be closed.

---

## Code of Conduct

Be professional.  
No ego-driven debates.  
Technical disagreements should be backed by data.

Harassment, hostility, or bad-faith behavior will not be tolerated.

---

## License

By contributing, you agree that your contributions will be licensed under the MIT License.
