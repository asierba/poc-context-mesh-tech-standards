# ARB — Architecture principles and service tiers

- **Date:** 2025-11-06, 14:00–15:10 UK
- **Attendees:** Priya Raman (Platform lead, ARB chair), Tom Okafor (Principal engineer, payments), Lena Fischer (Staff engineer, checkout), Marco Silva (Senior engineer, inventory), Hannah Moore (SRE lead), Sofia Lindqvist (VP Engineering)
- **Recording:** auto-generated transcript, lightly cleaned up

---

**[00:00] Priya Raman:** Today's the big one: the principles every service has to follow. I've got eight drafted. Deviations will need an exception ADR, as agreed last month.

**[00:12] Priya Raman:** One: teams own their data. A service's database is private to that service. Nobody else reads or writes it directly — you integrate through the API or events.

**[00:23] Marco Silva:** Search reads our inventory tables today.

**[00:26] Priya Raman:** Then that's the first migration. Two: async by default between domains. Cross-domain side effects go through Kafka events. Synchronous calls only when the caller needs the answer to carry on.

**[00:39] Lena Fischer:** Checkout charging a card is the obvious example. We can't create the order without the charge result.

**[00:45] Priya Raman:** Exactly — checkout → payments charge is the example I'll use. Three: every write API is idempotent. Clients send an `Idempotency-Key` header, servers keep keys for at least 24 hours.

**[00:58] Tom Okafor:** Payments already stores them for 24h. Fine by us.

**[01:02] Priya Raman:** Four: design for failure. Every outbound call has a timeout, bounded retries with exponential backoff, and a circuit breaker. Hannah, numbers?

**[01:11] Hannah Moore:** Default timeout two seconds. Max three retries. If a dependency needs more than two seconds regularly, that's a conversation, not a config change.

**[01:20] Lena Fischer:** Payments' p99 is over three seconds with 3-D Secure. We'd be timing out real charges.

**[01:26] Priya Raman:** Then checkout files an exception ADR. That's exactly what they're for. The default stays two.

**[01:32] Lena Fischer:** Fair, I'll write it up.

**[01:34] Priya Raman:** Five: stateless services. No local disk state. Session and cache data in Redis, durable state in Postgres.

**[01:42] Priya Raman:** Six: observable from day one. Structured JSON logs, OpenTelemetry traces, and RED metrics — rate, errors, duration — before a service goes to production.

**[01:52] Hannah Moore:** Before production, not "we'll add it after launch." I want that wording.

**[01:56] Priya Raman:** Kept. Seven: deployable independently. A service must be releasable without coordinating a release with another team.

**[02:04] Priya Raman:** Eight: buy before build for non-differentiating capabilities. Auth, email, feature flags, observability — use the approved vendors on the tech radar.

**[02:13] Sofia Lindqvist:** Good. Now tiers — Hannah.

**[02:15] Hannah Moore:** Three tiers. Tier 1 — checkout, payments, identity: 99.95% availability, 24/7 on-call, five-minute page ack. Tier 2 — search, recommendations, inventory: 99.9%, 24/7, fifteen-minute ack. Tier 3 — internal tools, reporting: 99.5%, business hours only.

**[02:36] Marco Silva:** Inventory is Tier 2? Checkout fails closed when we're down.

**[02:40] Hannah Moore:** For now. Bring an argument with data and we'll revisit.

**[02:44] Priya Raman:** Decisions: the eight principles as read — data ownership, async between domains, idempotent writes with `Idempotency-Key` stored 24h, design for failure with 2s default timeout, max 3 retries with exponential backoff and a circuit breaker, stateless with Redis and Postgres, observable before production, independently deployable, buy before build. Service tiers as Hannah described. Deviations need an exception ADR.

**[03:08] (agreed)**

## Actions

- Priya — publish architecture principles doc including the tier table.
- Lena — exception ADR for checkout's payments timeout.
- Marco — plan removal of search's direct reads on inventory tables.
