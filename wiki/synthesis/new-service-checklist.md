---
title: New Service Checklist
type: synthesis
created: 2026-09-30
updated: 2026-09-30
sources:
  - architecture-principles.md
  - tech-radar-2026-q3.md
  - adr-process.md
  - data-classification-policy.md
  - secrets-management-policy.md
  - authentication-policy.md
  - http-api-guidelines.md
  - incident-management-policy.md
---

# New Service Checklist

What the standards require before a new service goes to production, pulled together from several sources.

**Design**
- [ ] Pick a [service tier](../concepts/service-tiers.md) — it sets availability and on-call.
- [ ] Only Adopt tech, or an ADR for Trial/Hold ([Tech Radar](../standards/tech-radar-2026-q3.md), [ADR Process](../standards/adr-process.md)).
- [ ] ADR for any new synchronous cross-domain dependency.
- [ ] Data classification table in the design doc ([Data Classification](../concepts/data-classification.md)).

**Build**
- [ ] Private database; integrate via API or events ([Architecture Principles](../standards/architecture-principles.md)).
- [ ] Write APIs accept `Idempotency-Key` ([Idempotency](../concepts/idempotency.md)).
- [ ] Timeouts, bounded retries, circuit breakers ([Design for Failure](../concepts/design-for-failure.md)).
- [ ] Events via [transactional outbox](../concepts/transactional-outbox.md), CloudEvents + Avro.
- [ ] API follows [HTTP API Guidelines](../standards/http-api-guidelines.md) (money as minor units, error body, `/v1`).
- [ ] Secrets in [AWS Secrets Manager](../entities/aws-secrets-manager.md); `gitleaks` in CI.
- [ ] mTLS caller allow-list ([mTLS & Service Identity](../concepts/mtls-service-identity.md)).

**Operate**
- [ ] Structured JSON logs, OpenTelemetry traces, RED metrics.
- [ ] [PagerDuty](../entities/pagerduty.md) rota matching the tier.
