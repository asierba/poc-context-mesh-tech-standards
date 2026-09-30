---
title: Security council — Data classification (2026-03-12)
type: summary
created: 2026-09-30
updated: 2026-09-30
sources:
  - 2026-03-12-security-council-data-classification.md
---

# Security council — Data classification (2026-03-12)

Transcript: [2026-03-12-security-council-data-classification.md](../../raw/2026-03-12-security-council-data-classification.md). Resulting standard: [Data Classification Policy](../standards/data-classification-policy.md).

**Attendees:** Aisha Bello (Head of Security), Daniel Kim (Security engineer), Tom Okafor, Lena Fischer, Ben Carter.

## Decisions

- Four classes: Public, Internal, Confidential, Restricted; when in doubt, pick the higher class. See [Data Classification](../concepts/data-classification.md).
- Confidential in events only to consumers with a documented need — documented in the producing team's docs.
- Restricted never leaves the [vault](../entities/vault-service.md); others use tokens (out of PCI DSS scope). CVV never stored.
- Confidential retention: 24 months after last activity, or 30 days after verified GDPR erasure.
- Synthetic data only outside production; copying prod data is a disciplinary matter.
- Classification table in every new service's design doc.
