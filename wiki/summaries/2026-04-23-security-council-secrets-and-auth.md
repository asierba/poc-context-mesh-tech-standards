---
title: Security council — Secrets and authentication (2026-04-23)
type: summary
created: 2026-09-30
updated: 2026-09-30
sources:
  - 2026-04-23-security-council-secrets-and-auth.md
---

# Security council — Secrets and authentication (2026-04-23)

Transcript: [2026-04-23-security-council-secrets-and-auth.md](../../raw/2026-04-23-security-council-secrets-and-auth.md). Resulting standard: [Secrets Management Policy](../standards/secrets-management-policy.md) and [Authentication Policy](../standards/authentication-policy.md).

**Attendees:** Aisha Bello, Daniel Kim, Priya Raman, Hannah Moore, Tom Okafor.

## Why

- An API key leaked in March and turned out to be shared across three repos.
- A phishing attempt in February targeted SMS MFA.

## Decisions — secrets

- [AWS Secrets Manager](../entities/aws-secrets-manager.md) only; External Secrets Operator syncs into pods.
- Rotation: DB creds 30 days (automated), third-party keys 90 days, signing keys yearly.
- Humans via [break-glass](../concepts/break-glass-access.md) only: pages security, reviewed within 24h.
- `gitleaks` in CI and pre-commit blocks merges.
- Leak response: rotate → Sev2 → `#sec-incidents` → scrub history (after rotation).

## Decisions — authentication

- Customers: [Auth0](../entities/auth0.md), 15-min JWT, 30-day rotating refresh; `X-Acme-Customer-Id` trusted only from the gateway.
- Services: [Istio mTLS + SPIFFE allow-lists](../concepts/mtls-service-identity.md); plain HTTP blocked; no shared internal API keys.
- Staff: [Okta](../entities/okta.md) + YubiKey, no SMS MFA; just-in-time prod access, max 8h, ticket required.
