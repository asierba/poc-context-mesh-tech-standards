---
title: Incident Management Policy
type: standard
created: 2026-09-30
updated: 2026-09-30
sources:
  - 2026-01-15-sre-incident-process-review.md
---

# Incident Management Policy

Severity levels, incident process, paging. Decided in: [2026-01-15 meeting](../summaries/2026-01-15-sre-incident-process-review.md). Concept page: [Incident Severity](../concepts/incident-severity.md).

## Process

1. **Declare** — anyone, via `/incident` in Slack → `#inc-YYYYMMDD-short-name`.
2. **Command** — Sev1/Sev2 need a named Incident Commander (IC) from the IC rota, not the person fixing it.
3. **Communicate** — IC posts to `#incidents`; Sev1 also updates the public status page.
4. **Resolve** — mitigate first, root-cause later.
5. **Review** — blameless post-incident review within 5 business days (Sev1/Sev2); actions ticketed with owners and dates.

## Paging

- All paging via [PagerDuty](../entities/pagerduty.md); each team owns its rota (`checkout-prod`, `payments-prod`).
- Ack targets by [service tier](../concepts/service-tiers.md).
- **Change freeze:** no Tier 1 prod deploys from Black Friday − 7 days to Cyber Monday + 2 days without VP Engineering approval.
