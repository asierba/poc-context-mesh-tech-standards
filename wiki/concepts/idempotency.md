---
title: Idempotency
type: concept
created: 2026-09-30
updated: 2026-09-30
sources:
  - architecture-principles.md
  - event-conventions.md
  - http-api-guidelines.md
---

# Idempotency

Making a request or message safe to process more than once. Required on both sides of Acme's integrations.

- **Write APIs:** every write API is idempotent. Clients send an `Idempotency-Key` header; servers store keys for at least 24h ([Architecture Principles](../standards/architecture-principles.md), principle 3).
- **Key reuse with a different body:** `409` ([HTTP API Guidelines](../standards/http-api-guidelines.md)).
- **Retries:** clients may retry `5xx` only on idempotent requests.
- **Events:** delivery is at-least-once, so consumers dedupe on the CloudEvents `id` ([Event Conventions](../standards/event-conventions.md)).
- **Storage:** [Redis](../entities/redis.md) is the approved store for idempotency keys.
