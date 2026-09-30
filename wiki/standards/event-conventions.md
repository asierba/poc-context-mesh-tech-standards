---
title: Event Conventions
type: standard
created: 2026-09-30
updated: 2026-09-30
sources:
  - 2025-09-18-arb-event-conventions.md
---

# Event Conventions

Rules for every event on Acme's [Kafka](../entities/kafka.md) cluster. Decided in: [2025-09-18 meeting](../summaries/2025-09-18-arb-event-conventions.md).

- **Naming:** `<domain>.<past-tense-verb>` (`order.placed`, `payment.refunded`). Facts, not commands — `order.place` / `send-email` rejected. One event type per topic.
- **Envelope:** CloudEvents 1.0 (`specversion`, `id`, `source`, `type`, `time`, `dataschema`, `data`).
- **Schemas:** Avro in Confluent Schema Registry, `BACKWARD` compatibility. Breaking change → new major version published alongside the old one for ≥ 90 days.
- **Delivery:** at-least-once; consumers dedupe on event `id` ([Idempotency](../concepts/idempotency.md)).
- **Publishing:** via the [transactional outbox](../concepts/transactional-outbox.md); never directly from inside a DB transaction.
- **Retention:** 7 days default, 30 days for Tier 1 domains ([Service Tiers](../concepts/service-tiers.md)).
- **No Restricted data** in events ([Data Classification](../concepts/data-classification.md)).
