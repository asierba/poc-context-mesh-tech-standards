---
title: mTLS & Service Identity
type: concept
created: 2026-09-30
updated: 2026-09-30
sources:
  - authentication-policy.md
---

# mTLS & Service Identity

How services authenticate to each other ([Authentication Policy](../standards/authentication-policy.md)).

- All in-cluster traffic uses mTLS via [Istio](../entities/istio.md); plain HTTP is blocked by network policy.
- Authorisation uses the mesh's SPIFFE identity; each service lists allowed callers in its `AuthorizationPolicy`.
- No shared API keys between internal services.
- Customer identity is separate: the gateway forwards `X-Acme-Customer-Id`, trusted only from the gateway.
