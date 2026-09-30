---
title: Customer Data in Events
type: synthesis
created: 2026-09-30
updated: 2026-09-30
sources:
  - data-classification-policy.md
  - event-conventions.md
---

# Customer Data in Events

Can a Kafka event carry customer data? Combines [Data Classification Policy](../standards/data-classification-policy.md) and [Event Conventions](../standards/event-conventions.md).

| Data | Class | In events? |
|---|---|---|
| Customer ID, order ID | Internal | Yes |
| Email, name, address, phone | Confidential | Only to consumers with a **documented need** |
| Card number, CVV, passwords | Restricted | **Never** |

Things to watch:

- An event goes to every consumer of the topic. If only one consumer needs a Confidential field, everyone else still receives it.
- Topic retention (7 or 30 days, by [tier](../concepts/service-tiers.md)) must fit within the 30-day GDPR erasure window.
- Safer alternative: send only the ID and let the consumer that needs the data look it up.
