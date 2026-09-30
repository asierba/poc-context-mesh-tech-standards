---
title: Company-wide Glossary
type: synthesis
created: 2026-09-30
updated: 2026-09-30
sources:
  - 2025-10-02-arb-adr-process.md
  - 2025-09-18-arb-event-conventions.md
  - 2025-11-06-arb-architecture-principles.md
  - 2026-01-15-sre-incident-process-review.md
  - 2026-03-12-security-council-data-classification.md
---

# Company-wide Glossary

Acme-wide terms. Team-specific terms (e.g. payments' "settlement") live in each team's own glossary.

- **ARB** — see [ARB](../entities/arb.md).
- **ADR** — Architecture Decision Record; see [ADR process](../standards/adr-process.md).
- **Domain** — a business area owned by one team (checkout, payments, inventory); owns its services and data ([ADR process meeting](../summaries/2025-10-02-arb-adr-process.md)).
- **Exception ADR** — see [Exception ADR](../concepts/exception-adr.md).
- **IC** — Incident Commander; coordinates a Sev1/Sev2, doesn't fix it ([incident process review](../summaries/2026-01-15-sre-incident-process-review.md)).
- **Outbox** — see [Transactional Outbox](../concepts/transactional-outbox.md).
- **PAN** — Primary Account Number (card number). Restricted data ([data classification meeting](../summaries/2026-03-12-security-council-data-classification.md)).
- **Tier** — see [Service Tiers](../concepts/service-tiers.md).
- **Vault** — see [Vault Service](../entities/vault-service.md).
