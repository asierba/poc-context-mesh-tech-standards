# Company-wide Glossary

Terms used across Acme. Team-specific terms (e.g. payments' "settlement") live in each team's glossary.

- **ARB** — Architecture Review Board. Platform leads plus one rotating engineer from each domain. Approves ADRs and the tech radar.
- **ADR** — Architecture Decision Record. See [architecture/adr-process.md](architecture/adr-process.md).
- **Domain** — a business area owned by one team, e.g. checkout, payments, inventory. Each domain owns its services and data.
- **Exception ADR** — an approved, time-limited deviation from the architecture principles. Expires after 12 months.
- **IC** — Incident Commander. Coordinates a Sev1/Sev2 incident; doesn't fix it.
- **Outbox** — the transactional outbox pattern: write the event to a DB table in the same transaction as the state change, then relay it to Kafka.
- **PAN** — Primary Account Number, i.e. a card number. Restricted data.
- **Tier** — a service's criticality level (1–3), which sets its availability target and on-call expectations.
- **Vault** — the only service allowed to store Restricted payment data. Everyone else holds tokens.
