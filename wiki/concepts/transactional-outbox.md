---
title: Transactional Outbox
type: concept
created: 2026-09-30
updated: 2026-09-30
sources:
  - event-conventions.md
  - company-glossary.md
---

# Transactional Outbox

The mandatory way to publish events at Acme ([Event Conventions](../standards/event-conventions.md)).

- Write the event to an outbox table **in the same DB transaction** as the state change.
- A relay reads the table and publishes to [Kafka](../entities/kafka.md).
- Never publish directly from inside a DB transaction.
- Gives at-least-once delivery → consumers must be [idempotent](idempotency.md).

Glossary definition: [Company-wide Glossary](../synthesis/company-glossary.md).
