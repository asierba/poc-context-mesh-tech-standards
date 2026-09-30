# Acme — Tech Standards

Standards and policies that apply to every Acme engineering team. Owned by the platform team; changes go through the Architecture Review Board (ARB).

If a team's own docs contradict something here, this repo wins unless the team has an approved exception (see [architecture/adr-process.md](architecture/adr-process.md)).

## What's here

### Architecture
- [architecture/principles.md](architecture/principles.md) — architecture principles every service must follow.
- [architecture/tech-radar.md](architecture/tech-radar.md) — approved, trial, and banned technologies.
- [architecture/events.md](architecture/events.md) — event naming, schema, and Kafka conventions.
- [architecture/adr-process.md](architecture/adr-process.md) — when and how to write an ADR; exception process.

### Security
- [security/data-classification.md](security/data-classification.md) — data classes and handling rules.
- [security/secrets.md](security/secrets.md) — secrets management rules.
- [security/auth.md](security/auth.md) — service-to-service and user authentication.

### Engineering
- [engineering/api-guidelines.md](engineering/api-guidelines.md) — HTTP API conventions.
- [engineering/incident-management.md](engineering/incident-management.md) — severity levels and incident process.

### Reference
- [glossary.md](glossary.md) — company-wide terms.

## What's not here

Team-specific docs (APIs, runbooks, on-call rotas). Those live in each team's own repo.
