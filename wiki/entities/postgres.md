---
title: Postgres
type: entity
created: 2026-09-30
updated: 2026-09-30
sources:
  - tech-radar-2026-q3.md architecture-principles.md
---

# Postgres

Default relational store — Postgres 16 on managed RDS. **Adopt** ([Tech Radar](../standards/tech-radar-2026-q3.md)).

- Durable state for stateless services ([Architecture Principles](../standards/architecture-principles.md)).
- Each service's database is private to it.
- MySQL is on Hold — migrate to Postgres.
