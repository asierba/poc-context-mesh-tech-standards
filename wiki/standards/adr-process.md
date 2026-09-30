---
title: ADR Process
type: standard
created: 2026-09-30
updated: 2026-09-30
sources:
  - 2025-10-02-arb-adr-process.md
---

# ADR Process

When and how teams write Architecture Decision Records. Decided in: [2025-10-02 meeting](../summaries/2025-10-02-arb-adr-process.md).

## ADR required for

- Using a **Trial** or **Hold** technology ([tech radar](tech-radar-2026-q3.md)).
- A new **synchronous cross-domain dependency**.
- A **breaking change** to a public API or event schema.
- Any deviation from the [architecture principles](architecture-principles.md) → an [exception ADR](../concepts/exception-adr.md).

Not required for changes internal to one service.

## How

1. Copy the template into `docs/adr/NNNN-short-title.md` in the team's repo.
2. PR tagging `@acme/arb`.
3. [ARB](../entities/arb.md) reviews weekly (Thursdays); two approvals to accept.
4. Exception ADRs expire after 12 months.

Template sections: Status, Date, Context, Decision, Consequences, Alternatives considered.
