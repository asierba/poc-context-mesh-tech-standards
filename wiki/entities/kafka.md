---
title: Kafka
type: entity
created: 2026-09-30
updated: 2026-09-30
sources:
  - tech-radar-2026-q3.md event-conventions.md architecture-principles.md
---

# Kafka

Acme's event backbone. **Adopt** ring ([Tech Radar](../standards/tech-radar-2026-q3.md)).

- Carries all cross-domain events — async is the default between domains ([Architecture Principles](../standards/architecture-principles.md)).
- CloudEvents envelope, Avro schemas in Confluent Schema Registry ([Event Conventions](../standards/event-conventions.md)).
- Published only via the [transactional outbox](../concepts/transactional-outbox.md).
- Retention 7 days; 30 days for [Tier 1](../concepts/service-tiers.md).
