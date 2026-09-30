---
title: API guild — HTTP API guidelines (2025-12-04)
type: summary
created: 2026-09-30
updated: 2026-09-30
sources:
  - 2025-12-04-api-guild-http-guidelines.md
---

# API guild — HTTP API guidelines (2025-12-04)

Transcript: [2025-12-04-api-guild-http-guidelines.md](../../raw/2025-12-04-api-guild-http-guidelines.md). Resulting standard: [HTTP API Guidelines](../standards/http-api-guidelines.md).

**Attendees:** Raj Patel (API guild lead), Tom Okafor, Lena Fischer, Marco Silva, Priya Raman.

## Decisions

- JSON/HTTPS, `snake_case`, plural paths.
- Money as integer minor units + ISO 4217, never floats (payments had a rounding bug).
- ISO 8601 UTC timestamps; prefixed IDs.
- Path versioning; breaking changes bump version; old version ≥ 6 months; `Sunset` header.
- Standard error body `{error: {code, message, request_id}}`; status code baseline 400/401/403/404/409/422/429/5xx. Domain-specific codes (payments' 402) allowed with the standard body.
- Cursor pagination, max `limit` 200; no offset pagination.
