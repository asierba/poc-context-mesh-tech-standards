# Event Conventions

Applies to every event published on Acme's Kafka cluster.

## Naming

- Topic and event names: `<domain>.<past-tense-verb>` — e.g. `order.placed`, `payment.refunded`, `inventory.reserved`.
- Past tense only. Events describe facts, not commands. `order.place` or `send-email` are rejected in review.
- One event type per topic.

## Envelope

Every event uses the CloudEvents 1.0 envelope:

```json
{
  "specversion": "1.0",
  "id": "evt_01J9Z3K6X2",
  "source": "checkout-service",
  "type": "order.placed",
  "time": "2026-09-30T10:31:00Z",
  "dataschema": "acme://schemas/order.placed/v2",
  "data": { "...": "..." }
}
```

## Schemas

- Schemas are Avro, registered in the Confluent Schema Registry.
- Compatibility mode is `BACKWARD`. Adding optional fields is fine; removing or renaming fields is a breaking change.
- Breaking changes require a new major version (`order.placed.v3`) published alongside the old one for at least 90 days.

## Delivery

- At-least-once delivery. Consumers must be idempotent — dedupe on the event `id`.
- Publish via the transactional outbox pattern; never publish directly from inside a DB transaction.
- Retention: 7 days default; 30 days for Tier 1 domains.
- Events must not contain Restricted data (see [../security/data-classification.md](../security/data-classification.md)).
