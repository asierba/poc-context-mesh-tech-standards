# Data Classification

Every field a service stores or transmits falls into one of four classes. When in doubt, pick the higher class.

| Class | Examples | Storage | Logs | Events |
|---|---|---|---|---|
| **Public** | Product catalog, prices | Any | Allowed | Allowed |
| **Internal** | Order IDs, SKUs, internal metrics | Any Acme-managed store | Allowed | Allowed |
| **Confidential** | Customer name, email, shipping address, phone | Encrypted at rest | Masked (e.g. `j***@example.com`) | Allowed, only to consumers with a documented need |
| **Restricted** | Card numbers (PAN), CVV, passwords, government IDs | Only in approved vaults | **Never** | **Never** |

## Rules

- **Restricted data never leaves the vault service.** Other services handle tokens only. This keeps everything except the vault out of PCI DSS scope.
- CVV is never stored anywhere, not even in the vault.
- Confidential data retention: delete or anonymise 24 months after a customer's last activity, or within 30 days of a verified erasure (GDPR) request.
- Non-production environments use synthetic data only. Copying production Confidential or Restricted data to dev/staging is a disciplinary matter.
- Every new service's design doc must include a data classification table.
