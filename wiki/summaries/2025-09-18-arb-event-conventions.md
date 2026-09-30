---
title: ARB — Event conventions (2025-09-18)
type: summary
created: 2026-09-30
updated: 2026-09-30
sources:
  - 2025-09-18-arb-event-conventions.md
---

# ARB — Event conventions (2025-09-18)

Transcript: [2025-09-18-arb-event-conventions.md](../../raw/2025-09-18-arb-event-conventions.md). Resulting standard: [Event Conventions](../standards/event-conventions.md).

**Attendees:** Priya Raman (ARB chair), Tom Okafor (payments), Lena Fischer (checkout), Marco Silva (inventory), Ben Carter (data).

## Why

- Inconsistent topic names, commands disguised as events, three envelope shapes — data engineering couldn't consume reliably.
- Checkout lost `order.placed` events twice in Q4 2024 by publishing right after the DB insert; moved to an outbox in March 2025.

## Decisions

- Names `<domain>.<past-tense-verb>`; past tense only; one event type per topic.
- CloudEvents 1.0 envelope.
- Avro in Confluent Schema Registry, `BACKWARD` compatibility; breaking change → new major version kept alongside the old ≥ 90 days.
- At-least-once delivery; consumers dedupe on event `id`.
- Publish via [transactional outbox](../concepts/transactional-outbox.md), never from inside a DB transaction.
- Retention 7 days, 30 for Tier 1.
- No Restricted data in events.

## Actions

- Priya: publish the doc. Ben: list non-compliant topics. Marco: rename `inventory.reserve` → `inventory.reserved`.
