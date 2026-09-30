# Tech Radar

Reviewed quarterly by the ARB. Last review: 2026-Q3.

- **Adopt** — default choice; use without asking.
- **Trial** — allowed for new work; tell the ARB in your design doc.
- **Hold** — no new usage; existing usage may stay until migrated.
- **Banned** — must be removed; security or licensing reasons.

## Languages & runtimes

| Tech | Ring | Notes |
|---|---|---|
| TypeScript on Node 20+ | Adopt | Default for web and BFF services |
| Kotlin (JVM 21) | Adopt | Default for high-throughput backend services |
| Go | Trial | CLI tools and infra agents |
| Python 3.12 | Adopt | Data and ML only; not for request-path services |
| Node 16 / 18 | Banned | EOL; upgrade to 20+ |

## Data

| Tech | Ring | Notes |
|---|---|---|
| Postgres 16 | Adopt | Default relational store (managed RDS) |
| Redis 7 | Adopt | Cache, sessions, idempotency keys. Not a system of record |
| Kafka | Adopt | All cross-domain events (see [events.md](events.md)) |
| DynamoDB | Trial | Key-value workloads with >10k writes/s |
| MongoDB | Hold | Existing catalog service only |
| MySQL | Hold | Migrate to Postgres |

## Platform & tooling

| Tech | Ring | Notes |
|---|---|---|
| Kubernetes (EKS) | Adopt | All services |
| Terraform | Adopt | All infra; no click-ops in prod |
| GitHub Actions | Adopt | CI/CD |
| LaunchDarkly | Adopt | Feature flags |
| Datadog | Adopt | Metrics, logs, APM |
| Auth0 | Adopt | Customer identity |
| Jenkins | Banned | Decommissioned 2026-Q1 |
