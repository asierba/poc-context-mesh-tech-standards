---
title: HTTP API Guidelines
type: standard
created: 2026-09-30
updated: 2026-09-30
sources:
  - 2025-12-04-api-guild-http-guidelines.md
---

# HTTP API Guidelines

Conventions for every internal and external HTTP API. Decided in: [2025-12-04 meeting](../summaries/2025-12-04-api-guild-http-guidelines.md).

## Shape

- JSON over HTTPS, `snake_case` fields, plural resource paths (`/orders/{id}/items`).
- **Money:** integer minor units + ISO 4217 code (`{"amount_cents": 4999, "currency": "GBP"}`). Never floats.
- Timestamps ISO 8601 UTC. IDs prefixed (`ord_…`, `pay_…`, `cus_…`).

## Versioning

- Path versioning (`/v1/...`). Additive changes don't bump; breaking changes do.
- Old version supported ≥ 6 months after the new one ships. Deprecated endpoints send a `Sunset` header.

## Errors

- Body: `{"error": {"code", "message", "request_id"}}`.
- 400 invalid · 401 no/invalid credentials · 403 forbidden · 404 not found · 409 conflict (incl. [idempotency](../concepts/idempotency.md) key reuse) · 422 business rule failed · 429 rate limited + `Retry-After` · 5xx server error (clients may retry idempotent requests).

## Pagination

Cursor-based: `?limit=50&cursor=…`, response `next_cursor` (null on last page). Max `limit` 200.
