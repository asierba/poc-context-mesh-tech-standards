---
title: Data Classification Policy
type: standard
created: 2026-09-30
updated: 2026-09-30
sources:
  - 2026-03-12-security-council-data-classification.md
---

# Data Classification Policy

Four data classes and how each may be stored, logged, and sent in events. Decided in: [2026-03-12 meeting](../summaries/2026-03-12-security-council-data-classification.md). Concept page: [Data Classification](../concepts/data-classification.md).

| Class | Examples | Storage | Logs | Events |
|---|---|---|---|---|
| Public | Catalog, prices | Any | ✅ | ✅ |
| Internal | Order IDs, SKUs, metrics | Acme-managed | ✅ | ✅ |
| Confidential | Name, email, address, phone | Encrypted at rest | Masked | Only to consumers with a documented need |
| Restricted | PAN, CVV, passwords, gov IDs | Approved vaults only | Never | Never |

Rules:

- Restricted data never leaves the [vault](../entities/vault-service.md); others hold tokens (keeps them out of PCI DSS scope).
- CVV never stored, not even in the vault.
- Confidential retention: delete/anonymise 24 months after last activity, or within 30 days of a verified GDPR erasure request.
- Non-prod uses synthetic data only; copying prod Confidential/Restricted data is a disciplinary matter.
- Every new service's design doc includes a classification table.
