# ARB — Event conventions

- **Date:** 2025-09-18, 14:00–14:50 UK
- **Attendees:** Priya Raman (Platform lead, ARB chair), Tom Okafor (Principal engineer, payments), Lena Fischer (Staff engineer, checkout), Marco Silva (Senior engineer, inventory), Ben Carter (Data engineering)
- **Recording:** auto-generated transcript, lightly cleaned up

---

**[00:00] Priya Raman:** Okay, let's start, we've got a lot. The goal today is to agree one set of rules for everything on the Kafka cluster. Right now every team does its own thing and Ben's pipeline is paying for it.

**[00:14] Ben Carter:** Yeah. I've got topics called `OrderCreated`, `orders-v2`, `send-confirmation-email`… some are events, some are basically commands. And three different envelope shapes.

**[00:29] Priya Raman:** So, naming first. Proposal: `<domain>.<past-tense-verb>`. `order.placed`, `payment.refunded`, `inventory.reserved`.

**[00:38] Marco Silva:** Past tense only? We have `inventory.reserve` today.

**[00:42] Priya Raman:** Past tense only. Events are facts about something that already happened. If it reads like an instruction — `order.place`, `send-email` — it's a command and it gets rejected in review.

**[00:55] Tom Okafor:** Agree. And one event type per topic, please. Mixed topics make consumers write giant switch statements.

**[01:03] Priya Raman:** Noted — one event type per topic. Envelope: I'd like CloudEvents 1.0. `specversion`, `id`, `source`, `type`, `time`, `dataschema`, and the payload in `data`.

**[01:15] Ben Carter:** Yes please. Even just a consistent `id` and `time` would save me a week a quarter.

**[01:22] Lena Fischer:** Checkout already does that shape, so no objection. Our `dataschema` looks like `acme://schemas/order.placed/v2`.

**[01:30] Priya Raman:** Let's make that the example. Schemas — Avro, registered in the Confluent Schema Registry. Compatibility mode?

**[01:38] Tom Okafor:** `BACKWARD`. Adding optional fields is fine. Removing or renaming a field is a breaking change.

**[01:46] Marco Silva:** And when we do need to break something?

**[01:49] Priya Raman:** New major version — say `order.placed.v3` — published alongside the old one. How long do we keep both?

**[01:56] Ben Carter:** Ninety days minimum. Some of our batch consumers only get touched once a quarter.

**[02:03] Priya Raman:** Ninety days. Delivery guarantees — Lena, you had strong views.

**[02:08] Lena Fischer:** We learned this the hard way. Last Q4 checkout published `order.placed` straight after inserting the order, and twice the pod died between the insert and the publish. Orders fulfilment never heard about. We moved to a transactional outbox in March: write the event into an outbox table in the same DB transaction as the order, and a relay publishes it to Kafka afterwards.

**[02:31] Tom Okafor:** That should be the rule for everyone. Publish via the outbox, never directly from inside a DB transaction.

**[02:37] Lena Fischer:** The trade-off is you get at-least-once. The relay can publish and crash before it marks the row as sent.

**[02:44] Priya Raman:** So consumers must be idempotent — dedupe on the event `id`. That's fine, it's the envelope `id` we just agreed.

**[02:52] Marco Silva:** Retention?

**[02:54] Priya Raman:** Seven days default. Tier 1 domains get 30, so they can replay after a bad incident.

**[03:01] Tom Okafor:** One more — nothing Restricted in events. No card numbers, no CVV, nothing like that. Payments will reject any consumer that asks.

**[03:09] Priya Raman:** Agreed, and security will formalise the data classes separately. Let me read the decisions back.

**[03:14] Priya Raman:** Naming `<domain>.<past-tense-verb>`, past tense only, one event type per topic. CloudEvents 1.0 envelope. Avro in Confluent Schema Registry, `BACKWARD` compatibility, breaking changes get a new major version kept alongside the old for at least 90 days. At-least-once delivery, consumers dedupe on event `id`. Publish via transactional outbox, never from inside a DB transaction. Retention 7 days, 30 for Tier 1. No Restricted data in events. Anyone against?

**[03:40] (no objections)**

**[03:42] Priya Raman:** Great. I'll write it up as the event conventions doc.

## Actions

- Priya — publish event conventions doc.
- Ben — list non-compliant topic names for teams to fix.
- Marco — rename `inventory.reserve` → `inventory.reserved`.
