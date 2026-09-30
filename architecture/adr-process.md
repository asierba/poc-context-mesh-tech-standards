# ADR Process

## When an ADR is required

- Introducing a technology in the **Trial** or **Hold** ring of the [tech radar](tech-radar.md).
- Adding a new synchronous cross-domain dependency.
- Changing a public API or event schema in a breaking way.
- Any deviation from [principles.md](principles.md) — this is an **exception ADR**.

Not required for changes internal to one service that don't touch the above.

## How

1. Copy the template below into `docs/adr/NNNN-short-title.md` in your team's repo.
2. Open a PR and tag `@acme/arb`.
3. The ARB reviews weekly (Thursdays). Two ARB approvals are needed to accept.
4. Exception ADRs expire after 12 months and must be renewed or resolved.

## Template

```markdown
# NNNN — Title

Status: Proposed | Accepted | Superseded by NNNN
Date: YYYY-MM-DD

## Context
## Decision
## Consequences
## Alternatives considered
```
