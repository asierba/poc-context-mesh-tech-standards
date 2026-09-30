---
title: AWS Secrets Manager
type: entity
created: 2026-09-30
updated: 2026-09-30
sources:
  - secrets-management-policy.md
---

# AWS Secrets Manager

The only allowed place for secrets ([Secrets Management Policy](../standards/secrets-management-policy.md)).

- Synced into pods by the External Secrets Operator.
- Automated 30-day rotation for DB credentials; 90 days for third-party API keys; signing keys yearly.
- Human reads only through [break-glass access](../concepts/break-glass-access.md).
