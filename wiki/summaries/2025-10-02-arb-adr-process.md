---
title: ARB — ADR process (2025-10-02)
type: summary
created: 2026-09-30
updated: 2026-09-30
sources:
  - 2025-10-02-arb-adr-process.md
---

# ARB — ADR process (2025-10-02)

Transcript: [2025-10-02-arb-adr-process.md](../../raw/2025-10-02-arb-adr-process.md). Resulting standard: [ADR Process](../standards/adr-process.md).

**Attendees:** Priya Raman (ARB chair), Tom Okafor, Lena Fischer, Marco Silva, Sofia Lindqvist (VP Engineering).

## Context

- [ARB](../entities/arb.md) = platform leads + one rotating engineer per domain. A domain is a business area one team owns (checkout, payments, inventory), with its services and data.
- Aim: catch decisions that affect other teams, not approve everything.

## Decisions

- ADR required for: Trial/Hold tech; new sync cross-domain dependency; breaking public API or event schema change; any deviation from the principles ([exception ADR](../concepts/exception-adr.md)).
- Not required for changes internal to one service.
- Lives in the team repo `docs/adr/NNNN-short-title.md`; PR tagging `@acme/arb`.
- Weekly Thursday review; two approvals.
- Exception ADRs expire after 12 months.
- Template: Status, Date, Context, Decision, Consequences, Alternatives considered.
