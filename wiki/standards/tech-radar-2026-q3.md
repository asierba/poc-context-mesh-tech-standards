---
title: Tech Radar (2026-Q3)
type: standard
created: 2026-09-30
updated: 2026-09-30
sources:
  - 2026-07-09-arb-tech-radar-q3-review.md
---

# Tech Radar (2026-Q3)

Quarterly technology rings, reviewed by the [ARB](../entities/arb.md). Decided in: [2026-07-09 meeting](../summaries/2026-07-09-arb-tech-radar-q3-review.md).

## Rings

- **Adopt** — default; use without asking.
- **Trial** — allowed for new work; tell the ARB in your design doc. Needs an ADR ([ADR process](adr-process.md)).
- **Hold** — no new usage; existing may stay until migrated. Needs an ADR.
- **Banned** — must be removed.

## Placements

| Ring | Tech |
|---|---|
| Adopt | TypeScript on Node 20+ (web/BFF), Kotlin JVM 21 (high-throughput backend), Python 3.12 (data/ML only), [Postgres](../entities/postgres.md) 16, [Redis](../entities/redis.md) 7, [Kafka](../entities/kafka.md), Kubernetes (EKS), Terraform, GitHub Actions, LaunchDarkly, Datadog, [Auth0](../entities/auth0.md) |
| Trial | Go (CLI/infra agents), DynamoDB (> 10k writes/s) |
| Hold | MongoDB (catalog only), MySQL (migrate to Postgres) |
| Banned | Node 16/18 (EOL), Jenkins (decommissioned 2026-Q1) |
