# ARB — Tech radar 2026-Q3 review

- **Date:** 2026-07-09, 14:00–14:55 UK
- **Attendees:** Priya Raman (Platform lead, ARB chair), Tom Okafor (Principal engineer, payments), Lena Fischer (Staff engineer, checkout), Marco Silva (Senior engineer, inventory), Ben Carter (Data engineering)
- **Recording:** auto-generated transcript, lightly cleaned up

---

**[00:00] Priya Raman:** Quarterly radar review. Reminder of the rings: Adopt — default choice, use without asking. Trial — allowed for new work, tell the ARB in your design doc. Hold — no new usage, existing usage can stay until migrated. Banned — must be removed, for security or licensing reasons.

**[00:18] Priya Raman:** Languages and runtimes. TypeScript on Node 20+ stays Adopt, default for web and BFF services. Kotlin on JVM 21 stays Adopt, default for high-throughput backend services.

**[00:29] Marco Silva:** Go?

**[00:30] Priya Raman:** Trial, for CLI tools and infra agents. Python 3.12 is Adopt but for data and ML only — not request-path services.

**[00:38] Ben Carter:** That's fine for us.

**[00:39] Priya Raman:** Node 16 and 18 are Banned. They're end of life — upgrade to 20+.

**[00:44] Priya Raman:** Data. Postgres 16 Adopt, the default relational store on managed RDS. Redis 7 Adopt, for cache, sessions, idempotency keys — and it's not a system of record.

**[00:55] Tom Okafor:** Kafka Adopt for all cross-domain events, per the event conventions.

**[00:59] Priya Raman:** Yes. DynamoDB stays Trial, for key-value workloads above ten thousand writes a second.

**[01:05] Marco Silva:** And Mongo?

**[01:06] Priya Raman:** Hold. Existing catalog service only. MySQL is also Hold — migrate to Postgres.

**[01:12] Priya Raman:** Platform and tooling. Kubernetes on EKS, Adopt, all services. Terraform Adopt — all infra, no click-ops in prod. GitHub Actions Adopt for CI/CD. LaunchDarkly for feature flags, Datadog for metrics, logs and APM, Auth0 for customer identity — all Adopt.

**[01:30] Tom Okafor:** Jenkins?

**[01:31] Priya Raman:** Banned. We decommissioned it in Q1.

**[01:34] Lena Fischer:** Can we talk about Next.js? Checkout's been running it on Trial under our ADR since last year.

**[01:39] Priya Raman:** Not today — frameworks aren't on the radar yet. Let's put it on the Q4 agenda.

**[01:44] Priya Raman:** Decisions: radar as read. Adopt — TypeScript/Node 20+, Kotlin JVM 21, Python 3.12 for data/ML only, Postgres 16, Redis 7, Kafka, EKS, Terraform, GitHub Actions, LaunchDarkly, Datadog, Auth0. Trial — Go, DynamoDB. Hold — MongoDB, MySQL. Banned — Node 16/18, Jenkins. Next review 2026-Q4.

**[02:05] (agreed)**

## Actions

- Priya — publish the 2026-Q3 radar.
- Priya — add web frameworks (Next.js) to the Q4 agenda.
