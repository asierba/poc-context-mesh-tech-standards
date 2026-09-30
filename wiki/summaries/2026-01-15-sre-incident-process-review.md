---
title: SRE review — Incident process after Black Friday (2026-01-15)
type: summary
created: 2026-09-30
updated: 2026-09-30
sources:
  - 2026-01-15-sre-incident-process-review.md
---

# SRE review — Incident process after Black Friday (2026-01-15)

Transcript: [2026-01-15-sre-incident-process-review.md](../../raw/2026-01-15-sre-incident-process-review.md). Resulting standard: [Incident Management Policy](../standards/incident-management-policy.md).

**Attendees:** Hannah Moore (SRE lead), Sofia Lindqvist, Lena Fischer, Tom Okafor, Aisha Bello (Head of Security).

## Why

- Two peak-season incidents with nobody clearly in charge; fixers also doing exec updates.
- A Black Friday deploy broke checkout.

## Decisions

- [Severity levels](../concepts/incident-severity.md) Sev1/2/3; leaked secret listed as a Sev2 example.
- Process: declare with `/incident` (anyone) → named IC for Sev1/2 who isn't fixing → IC communicates (`#incidents`, status page for Sev1) → mitigate first → blameless review within 5 business days, actions ticketed.
- All paging via [PagerDuty](../entities/pagerduty.md); team-owned rotas; acks by tier.
- Tier 1 change freeze: Black Friday − 7 days to Cyber Monday + 2 days, unless VP Engineering approves.
