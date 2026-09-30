---
title: Data Classification
type: concept
created: 2026-09-30
updated: 2026-09-30
sources:
  - data-classification-policy.md
  - event-conventions.md
  - company-glossary.md
---

# Data Classification

Every stored or transmitted field is Public, Internal, Confidential, or Restricted. When in doubt, pick the higher class. Full table: [Data Classification Policy](../standards/data-classification-policy.md).

Key consequences:

- **Confidential** (email, name, address, phone): encrypted at rest, masked in logs, allowed in events **only to consumers with a documented need**.
- **Restricted** (PAN, CVV, passwords, gov IDs): only in the [vault](../entities/vault-service.md); never in logs or events ([Event Conventions](../standards/event-conventions.md)).
- Retention: Confidential data deleted/anonymised after 24 months of inactivity or within 30 days of a GDPR erasure request.
- New services must include a classification table in their design doc.

See also: [Customer Data in Events](../synthesis/customer-data-in-events.md).
