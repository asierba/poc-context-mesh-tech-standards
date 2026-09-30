---
title: PagerDuty
type: entity
created: 2026-09-30
updated: 2026-09-30
sources:
  - incident-management-policy.md architecture-principles.md
---

# PagerDuty

All paging goes through PagerDuty ([Incident Management Policy](../standards/incident-management-policy.md)).

- Each team owns its rota, e.g. `checkout-prod`, `payments-prod`.
- Ack targets by [service tier](../concepts/service-tiers.md): 5 min (Tier 1), 15 min (Tier 2), business hours (Tier 3).
