---
title: Architecture Principles
type: standard
created: 2026-09-30
updated: 2026-09-30
sources:
  - 2025-11-06-arb-architecture-principles.md
---

# Architecture Principles

Eight principles every Acme service must follow. Deviations need an [exception ADR](../concepts/exception-adr.md). Decided in: [2025-11-06 meeting](../summaries/2025-11-06-arb-architecture-principles.md).

1. **Teams own their data** — a service's DB is private; integrate via API or events.
2. **Async by default between domains** — cross-domain side effects go through [Kafka](../entities/kafka.md). Sync only when the caller needs the answer to continue (e.g. checkout → payments charge).
3. **Every write API is idempotent** — `Idempotency-Key` header, keys stored ≥ 24h. See [Idempotency](../concepts/idempotency.md).
4. **Design for failure** — timeout (default 2s), max 3 retries with exponential backoff, circuit breaker. See [Design for Failure](../concepts/design-for-failure.md).
5. **Stateless services** — sessions/cache in [Redis](../entities/redis.md), durable state in [Postgres](../entities/postgres.md).
6. **Observable from day one** — structured JSON logs, OpenTelemetry traces, RED metrics before production.
7. **Deployable independently** — no coordinated releases across teams.
8. **Buy before build** for non-differentiating capabilities (auth, email, flags, observability) — approved vendors on the [tech radar](tech-radar-2026-q3.md).

Also defines [service tiers](../concepts/service-tiers.md) (availability + on-call by tier).
