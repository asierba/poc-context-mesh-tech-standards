# Acme Tech Standards Wiki — Schema

LLM-maintained wiki of Acme's company-wide engineering standards.

## Structure

```
raw/        # Meeting transcripts (ARB, security council, guilds, SRE reviews). Immutable — never edited by the LLM.
wiki/       # LLM-maintained markdown pages. The LLM owns this layer entirely.
index.md    # Category-organized catalog of all wiki pages.
log.md      # Append-only chronological activity log.
```

## Page types

- **Summary** — digest of one meeting transcript: attendees, why, decisions, actions. `wiki/summaries/`, filename matches the raw file.
- **Standard** — the current, consolidated rule set on one topic (principles, tech radar, secrets…), distilled from the meetings that decided it. `wiki/standards/`. This is what teams must follow.
- **Concept** — a cross-cutting idea (idempotency, service tiers). `wiki/concepts/`.
- **Entity** — a tool, service, or body (Kafka, Auth0, ARB). `wiki/entities/`.
- **Synthesis** — combines several sources into a reusable answer (new-service checklist). `wiki/synthesis/`.

## Conventions

- Every page starts with YAML frontmatter: `title`, `type`, `created`, `updated`, `sources`.
- Cross-references are relative markdown links with the `.md` extension. No `[[wikilinks]]`.
- Summaries cite raw transcripts (`../../raw/…`). Standards cite the meeting summaries that decided them. Concepts, entities, and synthesis cite standards or summaries. Chain: concept/entity/synthesis → standard → summary → raw transcript.
- Transcripts are authoritative. If a wiki page disagrees with what was decided in `raw/`, the transcript wins — fix the page. When a later meeting changes a decision, update the standard and note the superseding meeting.
- Keep pages short. Bullets over prose.

## Workflows

- **Ingest** — a new transcript lands in `raw/`: write its summary, update the affected standards and concept/entity/synthesis pages, update `index.md`, append to `log.md`.
- **Query** — start at `index.md`, read the relevant standards and wiki pages; for *why* a rule exists, follow the chain to the meeting summary and transcript. Cite the pages used.
- **Lint** — check for broken links, pages missing from `index.md`, and wiki pages that contradict `raw/`.
