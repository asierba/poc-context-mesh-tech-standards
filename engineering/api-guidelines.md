# HTTP API Guidelines

Applies to every HTTP API, internal or external.

## Shape

- JSON over HTTPS. Field names in `snake_case`.
- Resource paths are plural nouns: `/orders`, `/orders/{id}/items`.
- Money is always an integer in minor units plus an ISO 4217 currency code: `{"amount_cents": 4999, "currency": "GBP"}`. Never floats.
- Timestamps are ISO 8601 in UTC: `2026-09-30T10:31:00Z`.
- IDs are prefixed strings: `ord_…`, `pay_…`, `cus_…`.

## Versioning

- Version in the path: `/v1/orders`.
- Additive changes don't need a new version. Breaking changes do, and the old version is supported for at least 6 months after the new one ships.
- Deprecated endpoints return a `Sunset` header with the removal date.

## Errors

All errors use this body:

```json
{
  "error": {
    "code": "idempotency_conflict",
    "message": "Idempotency key reused with a different request body.",
    "request_id": "req_8f2c1"
  }
}
```

Standard status codes:

| Status | Meaning |
|---|---|
| 400 | Invalid request body or params |
| 401 | Missing or invalid credentials |
| 403 | Authenticated but not allowed |
| 404 | Resource not found |
| 409 | Conflict (including idempotency key reuse) |
| 422 | Valid request, failed business rule |
| 429 | Rate limited — include `Retry-After` |
| 5xx | Server error — clients may retry idempotent requests |

## Pagination

Cursor-based: `?limit=50&cursor=…`. Responses include `next_cursor` (null on the last page). Max `limit` is 200.
