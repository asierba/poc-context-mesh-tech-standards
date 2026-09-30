---
title: Incident Severity
type: concept
created: 2026-09-30
updated: 2026-09-30
sources:
  - incident-management-policy.md
  - secrets-management-policy.md
---

# Incident Severity

Three levels ([Incident Management Policy](../standards/incident-management-policy.md)).

| Sev | Definition | Example | Response |
|---|---|---|---|
| Sev1 | Customers can't buy, or data breach suspected | Checkout down, payments failing > 5% | Page immediately; IC within 10 min; exec update every 30 min |
| Sev2 | Major feature degraded, or Tier 1 at risk | Search down, secret leaked | Page owning team; hourly updates |
| Sev3 | Minor degradation, workaround exists | Slow recommendations | Ticket; fix within 5 business days |

- Sev1/Sev2 need an Incident Commander and a post-incident review within 5 business days.
- A leaked secret is always Sev2 ([Secrets Management Policy](../standards/secrets-management-policy.md)).
