# Secrets Management

## Rules

- All secrets live in **AWS Secrets Manager**. Nowhere else — not in env files, repos, CI variables, or Kubernetes Secrets manifests.
- Services read secrets at startup via the External Secrets Operator, which syncs them into the pod.
- **Rotation:** database credentials every 30 days (automated); third-party API keys every 90 days; signing keys yearly.
- Humans get production secret access only through a break-glass role, which pages the security on-call and is reviewed within 24h.
- `gitleaks` runs in every repo's CI and as a pre-commit hook. A detected secret blocks the merge.

## If a secret leaks

1. Rotate it immediately — don't wait to confirm exposure.
2. Open a Sev2 incident (see [../engineering/incident-management.md](../engineering/incident-management.md)).
3. Tell security in `#sec-incidents`.
4. Scrub it from git history after rotation, not before.
