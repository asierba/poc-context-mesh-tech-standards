---
title: Break-glass Access
type: concept
created: 2026-09-30
updated: 2026-09-30
sources:
  - secrets-management-policy.md
  - authentication-policy.md
---

# Break-glass Access

The only way for a human to read production secrets ([Secrets Management Policy](../standards/secrets-management-policy.md)).

- Using the break-glass role pages the security on-call.
- Every use is reviewed within 24h.
- Separate from normal just-in-time production access (max 8h, linked ticket) via the access portal ([Authentication Policy](../standards/authentication-policy.md)).
