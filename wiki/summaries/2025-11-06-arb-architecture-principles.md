---
title: ARB — Architecture principles and service tiers (2025-11-06)
type: summary
created: 2026-09-30
updated: 2026-09-30
sources:
  - 2025-11-06-arb-architecture-principles.md
---

# ARB — Architecture principles and service tiers (2025-11-06)

Transcript: [2025-11-06-arb-architecture-principles.md](../../raw/2025-11-06-arb-architecture-principles.md). Resulting standard: [Architecture Principles](../standards/architecture-principles.md).

**Attendees:** Priya Raman (ARB chair), Tom Okafor, Lena Fischer, Marco Silva, Hannah Moore (SRE lead), Sofia Lindqvist.

## Decisions

- Eight principles: data ownership; async between domains (sync only when the caller needs the answer, e.g. checkout → payments charge); idempotent writes (`Idempotency-Key`, ≥ 24h); design for failure; stateless (Redis/Postgres); observable **before** production; independently deployable; buy before build.
- [Design for failure](../concepts/design-for-failure.md) numbers from SRE: 2s default timeout, max 3 retries with exponential backoff, circuit breaker.
- [Service tiers](../concepts/service-tiers.md): Tier 1 99.95% / 5-min ack; Tier 2 99.9% / 15-min; Tier 3 99.5% / business hours.
- Deviations need an [exception ADR](../concepts/exception-adr.md).

## Notable discussion

- Checkout's payments calls have p99 > 3s (3-D Secure) → told to file an exception ADR rather than change the default.
- Search reads inventory's tables directly → first migration under principle 1.
- Inventory questioned being Tier 2 given checkout fails closed without it; SRE asked for data.
