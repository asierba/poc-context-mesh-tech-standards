---
title: Authentication Policy
type: standard
created: 2026-09-30
updated: 2026-09-30
sources:
  - 2026-04-23-security-council-secrets-and-auth.md
---

# Authentication Policy

How customers, services, and staff authenticate. Decided in: [2026-04-23 meeting](../summaries/2026-04-23-security-council-secrets-and-auth.md).

## Customers

- Identity via [Auth0](../entities/auth0.md); services never store customer passwords.
- Access token: JWT, 15 min. Refresh token: 30 days, rotating.
- API gateway validates the JWT and sets `X-Acme-Customer-Id`; backends trust it **only** from the gateway.

## Service-to-service

- [mTLS via Istio](../concepts/mtls-service-identity.md) for all in-cluster traffic; plain HTTP blocked.
- Authorisation by SPIFFE identity; per-service caller allow-list in `AuthorizationPolicy`.
- No shared API keys between internal services.

## Staff

- [Okta](../entities/okta.md) SSO with YubiKey MFA; no SMS MFA.
- Production access is just-in-time, max 8 hours, linked ticket required.
