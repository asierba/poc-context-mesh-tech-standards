# Architecture Principles

Every service must follow these. Deviations need an approved ADR exception.

1. **Teams own their data.** A service's database is private to that service. No other service reads or writes it directly — integrate via API or events.
2. **Async by default between domains.** Cross-domain side effects go through Kafka events. Synchronous calls are allowed only when the caller needs the answer to continue (e.g. checkout → payments charge).
3. **Every write API is idempotent.** Clients send an `Idempotency-Key` header; servers store keys for at least 24h.
4. **Design for failure.** Every outbound call has a timeout (default 2s), bounded retries with exponential backoff (max 3), and a circuit breaker.
5. **Stateless services.** No local disk state. Session and cache data go in Redis; durable state in Postgres.
6. **Observable from day one.** Structured JSON logs, OpenTelemetry traces, and RED metrics (rate, errors, duration) are required before a service goes to production.
7. **Deployable independently.** A service must be releasable without coordinating a release with another team.
8. **Buy before build for non-differentiating capabilities.** Auth, email, feature flags, and observability use approved vendors (see [tech-radar.md](tech-radar.md)).

## Service tiers

| Tier | Examples | Availability target | On-call |
|---|---|---|---|
| Tier 1 | checkout, payments, identity | 99.95% | 24/7, 5-min page ack |
| Tier 2 | search, recommendations, inventory | 99.9% | 24/7, 15-min page ack |
| Tier 3 | internal tools, reporting | 99.5% | Business hours |
