# Index

Catalog of every page in the wiki. Standards are the current rules; meeting summaries explain why. See [CLAUDE.md](CLAUDE.md) for page types and conventions.

## Architecture

- [Architecture Principles](wiki/standards/architecture-principles.md) — the eight principles every service must follow.
- [Tech Radar (2026-Q3)](wiki/standards/tech-radar-2026-q3.md) — Adopt / Trial / Hold / Banned technologies.
- [Event Conventions](wiki/standards/event-conventions.md) — Kafka naming, CloudEvents envelope, Avro schemas, delivery.
- [ADR Process](wiki/standards/adr-process.md) — when an ADR is required and how the ARB approves it.
- [Service Tiers](wiki/concepts/service-tiers.md) — availability targets and on-call by tier.
- [Design for Failure](wiki/concepts/design-for-failure.md) — timeouts, retries, circuit breakers.
- [Idempotency](wiki/concepts/idempotency.md) — `Idempotency-Key`, 409 on reuse, dedupe on event id.
- [Transactional Outbox](wiki/concepts/transactional-outbox.md) — the mandatory way to publish events.
- [Exception ADR](wiki/concepts/exception-adr.md) — time-limited deviations from the principles.

## Security

- [Data Classification Policy](wiki/standards/data-classification-policy.md) — Public / Internal / Confidential / Restricted.
- [Secrets Management Policy](wiki/standards/secrets-management-policy.md) — storage, rotation, leak response.
- [Authentication Policy](wiki/standards/authentication-policy.md) — customers, service-to-service, staff.
- [Data Classification](wiki/concepts/data-classification.md) — what each class means in practice.
- [mTLS & Service Identity](wiki/concepts/mtls-service-identity.md) — Istio mTLS and SPIFFE allow-lists.
- [Break-glass Access](wiki/concepts/break-glass-access.md) — human access to production secrets.

## Engineering

- [HTTP API Guidelines](wiki/standards/http-api-guidelines.md) — shape, money, versioning, errors, pagination.
- [Incident Management Policy](wiki/standards/incident-management-policy.md) — process, paging, change freeze.
- [Incident Severity](wiki/concepts/incident-severity.md) — Sev1 / Sev2 / Sev3.

## Entities

- [ARB](wiki/entities/arb.md) · [Kafka](wiki/entities/kafka.md) · [Postgres](wiki/entities/postgres.md) · [Redis](wiki/entities/redis.md) · [Auth0](wiki/entities/auth0.md) · [AWS Secrets Manager](wiki/entities/aws-secrets-manager.md) · [Istio](wiki/entities/istio.md) · [Okta](wiki/entities/okta.md) · [PagerDuty](wiki/entities/pagerduty.md) · [Vault Service](wiki/entities/vault-service.md)

## Synthesis

- [New Service Checklist](wiki/synthesis/new-service-checklist.md) — everything a new service needs before production.
- [Customer Data in Events](wiki/synthesis/customer-data-in-events.md) — what customer data may go in Kafka events.

## Meetings

- [2025-09-18 ARB — Event conventions](wiki/summaries/2025-09-18-arb-event-conventions.md)
- [2025-10-02 ARB — ADR process](wiki/summaries/2025-10-02-arb-adr-process.md)
- [2025-11-06 ARB — Architecture principles and service tiers](wiki/summaries/2025-11-06-arb-architecture-principles.md)
- [2025-12-04 API guild — HTTP API guidelines](wiki/summaries/2025-12-04-api-guild-http-guidelines.md)
- [2026-01-15 SRE review — Incident process after Black Friday](wiki/summaries/2026-01-15-sre-incident-process-review.md)
- [2026-03-12 Security council — Data classification](wiki/summaries/2026-03-12-security-council-data-classification.md)
- [2026-04-23 Security council — Secrets and authentication](wiki/summaries/2026-04-23-security-council-secrets-and-auth.md)
- [2026-07-09 ARB — Tech radar 2026-Q3 review](wiki/summaries/2026-07-09-arb-tech-radar-q3-review.md)

## Reference

- [Company-wide Glossary](wiki/synthesis/company-glossary.md) — Acme-wide terms.
