---
title: Design for Failure
type: concept
created: 2026-09-30
updated: 2026-09-30
sources:
  - architecture-principles.md
  - http-api-guidelines.md
---

# Design for Failure

Principle 4 of the [architecture principles](../standards/architecture-principles.md). Every outbound call has:

- a **timeout** — default 2s;
- **bounded retries** — exponential backoff, max 3;
- a **circuit breaker**.

Related:

- Only retry `5xx` on [idempotent](idempotency.md) requests; honour `Retry-After` on `429` ([HTTP API Guidelines](../standards/http-api-guidelines.md)).
- A non-default timeout is a deviation → needs an [exception ADR](exception-adr.md).
