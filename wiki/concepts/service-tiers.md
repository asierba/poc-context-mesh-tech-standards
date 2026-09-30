---
title: Service Tiers
type: concept
created: 2026-09-30
updated: 2026-09-30
sources:
  - architecture-principles.md
  - incident-management-policy.md
  - event-conventions.md
---

# Service Tiers

A service's criticality level (1–3). Sets its availability target, on-call expectations, and some retention rules. Defined in [Architecture Principles](../standards/architecture-principles.md).

| Tier | Examples | Availability | On-call |
|---|---|---|---|
| 1 | checkout, payments, identity | 99.95% | 24/7, 5-min page ack |
| 2 | search, recommendations, inventory | 99.9% | 24/7, 15-min page ack |
| 3 | internal tools, reporting | 99.5% | Business hours |

Tier-dependent rules elsewhere:

- Kafka topic retention: 30 days for Tier 1, 7 days otherwise ([Event Conventions](../standards/event-conventions.md)).
- Black Friday change freeze applies to Tier 1 services ([Incident Management](../standards/incident-management-policy.md)).
- Page ack targets come from the tier ([PagerDuty](../entities/pagerduty.md)).
