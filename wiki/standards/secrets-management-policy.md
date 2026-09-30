---
title: Secrets Management Policy
type: standard
created: 2026-09-30
updated: 2026-09-30
sources:
  - 2026-04-23-security-council-secrets-and-auth.md
---

# Secrets Management Policy

Where secrets live, how they rotate, and what to do on a leak. Decided in: [2026-04-23 meeting](../summaries/2026-04-23-security-council-secrets-and-auth.md).

- **Storage:** [AWS Secrets Manager](../entities/aws-secrets-manager.md) only — not env files, repos, CI variables, or Kubernetes Secrets manifests.
- **Delivery:** External Secrets Operator syncs secrets into pods at startup.
- **Rotation:** DB credentials every 30 days (automated); third-party API keys every 90 days; signing keys yearly.
- **Human access:** only via [break-glass](../concepts/break-glass-access.md) role — pages security on-call, reviewed within 24h.
- **Detection:** `gitleaks` in CI and pre-commit; a hit blocks the merge.

## On a leak

1. Rotate immediately — don't wait to confirm exposure.
2. Open a **Sev2** ([Incident Severity](../concepts/incident-severity.md)).
3. Tell security in `#sec-incidents`.
4. Scrub git history **after** rotation.
