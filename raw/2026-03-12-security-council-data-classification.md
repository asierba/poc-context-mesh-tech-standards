# Security council — Data classification

- **Date:** 2026-03-12, 10:00–10:50 UK
- **Attendees:** Aisha Bello (Head of Security), Daniel Kim (Security engineer), Tom Okafor (Principal engineer, payments), Lena Fischer (Staff engineer, checkout), Ben Carter (Data engineering)
- **Recording:** auto-generated transcript, lightly cleaned up

---

**[00:00] Aisha Bello:** We promised the ARB a proper data classification. Four classes; every field a service stores or transmits falls into one. And the tie-breaker: when in doubt, pick the higher class.

**[00:13] Daniel Kim:** Public: product catalog, prices. Store anywhere, log it, put it in events.

**[00:19] Daniel Kim:** Internal: order IDs, SKUs, internal metrics. Any Acme-managed store, logs fine, events fine.

**[00:26] Daniel Kim:** Confidential: customer name, email, shipping address, phone. Encrypted at rest. Masked in logs — like `j***@example.com`. In events only to consumers with a documented need.

**[00:39] Ben Carter:** "Documented need" — documented where?

**[00:42] Aisha Bello:** In the producing team's docs. If you can't say who needs it and why, it doesn't go in the event.

**[00:48] Daniel Kim:** Restricted: card numbers — PAN, the primary account number — CVV, passwords, government IDs. Only in approved vaults. Never in logs. Never in events.

**[00:59] Tom Okafor:** Which is how payments works already. Restricted data never leaves the vault service; everyone else handles tokens. It keeps every other service out of PCI DSS scope.

**[01:09] Aisha Bello:** Write that down as a rule. And CVV is never stored anywhere — not even in the vault.

**[01:15] Lena Fischer:** Retention for Confidential?

**[01:17] Aisha Bello:** Delete or anonymise 24 months after a customer's last activity, or within 30 days of a verified GDPR erasure request.

**[01:25] Ben Carter:** And test data? Some teams copy prod into staging.

**[01:28] Aisha Bello:** Not any more. Non-production uses synthetic data only. Copying production Confidential or Restricted data to dev or staging is a disciplinary matter.

**[01:37] Daniel Kim:** Last one: every new service's design doc includes a data classification table.

**[01:42] Aisha Bello:** Decisions: four classes — Public, Internal, Confidential, Restricted — with the storage, logging, and events rules as read; when in doubt pick the higher class. Restricted never leaves the vault; others use tokens, out of PCI DSS scope. CVV never stored. Confidential retention 24 months after last activity or 30 days after a verified erasure request. Synthetic data only outside production. Classification table in every new service's design doc.

**[02:05] (agreed)**

## Actions

- Daniel — publish the data classification doc.
- Ben — audit staging databases for production copies.
