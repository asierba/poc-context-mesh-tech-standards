# Acme — Tech Standards Wiki

Company-wide engineering standards for every Acme team, kept as an **LLM-maintained wiki**. Owned by the platform team; policy changes go through the Architecture Review Board (ARB).

If a team's own docs contradict these standards, the standards win unless the team has an approved exception ADR.

## Start here

- [index.md](index.md) — catalog of every wiki page, by category.
- [log.md](log.md) — what changed and when.
- [CLAUDE.md](CLAUDE.md) — how the wiki is structured and maintained.

## Layout

```
raw/     # Meeting transcripts where standards were decided. Immutable.
wiki/    # LLM-maintained pages derived from raw/
  standards/   # the current rules — what teams must follow
  summaries/   # one digest per meeting: why, decisions, actions
  concepts/    # cross-cutting ideas (idempotency, service tiers, …)
  entities/    # tools, services, and bodies (Kafka, Auth0, ARB, …)
  synthesis/   # higher-level pages combining several sources
```

## What's not here

Team-specific docs (APIs, runbooks, on-call rotas). Those live in each team's own repo.
