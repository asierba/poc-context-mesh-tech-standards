# API guild — HTTP API guidelines

- **Date:** 2025-12-04, 11:00–11:45 UK
- **Attendees:** Raj Patel (API guild lead), Tom Okafor (Principal engineer, payments), Lena Fischer (Staff engineer, checkout), Marco Silva (Senior engineer, inventory), Priya Raman (Platform lead)
- **Recording:** auto-generated transcript, lightly cleaned up

---

**[00:00] Raj Patel:** Morning. Goal: one set of HTTP conventions for every API, internal or external. I'll go section by section.

**[00:09] Raj Patel:** Shape. JSON over HTTPS. Field names `snake_case`.

**[00:13] Marco Silva:** Inventory is camelCase today…

**[00:16] Raj Patel:** New versions switch. Resource paths are plural nouns — `/orders`, `/orders/{id}/items`.

**[00:23] Tom Okafor:** Money. Please. Integer in minor units plus an ISO 4217 currency code. `{"amount_cents": 4999, "currency": "GBP"}`. Never floats. We had a rounding bug last year that cost real money.

**[00:36] Raj Patel:** Agreed, never floats. Timestamps ISO 8601 in UTC, like `2026-09-30T10:31:00Z`. IDs are prefixed strings — `ord_`, `pay_`, `cus_`.

**[00:47] Raj Patel:** Versioning. Version in the path, `/v1/orders`. Additive changes don't need a new version. Breaking changes do.

**[00:55] Lena Fischer:** How long do we support the old one?

**[00:57] Raj Patel:** At least six months after the new one ships. And deprecated endpoints send a `Sunset` header with the removal date.

**[01:05] Raj Patel:** Errors. One body shape everywhere: an `error` object with `code`, `message`, `request_id`. Example code: `idempotency_conflict`, message "Idempotency key reused with a different request body."

**[01:17] Raj Patel:** Status codes: 400 invalid body or params. 401 missing or invalid credentials. 403 authenticated but not allowed. 404 not found. 409 conflict — including idempotency key reuse. 422 valid request but a business rule failed. 429 rate limited, with `Retry-After`. 5xx server error — clients may retry idempotent requests.

**[01:40] Tom Okafor:** Payments returns 402 for declined cards. Keep that?

**[01:43] Raj Patel:** Domain-specific codes are fine as long as they use the standard error body. The list is the baseline.

**[01:49] Raj Patel:** Pagination: cursor-based. `?limit=50&cursor=…`, response includes `next_cursor`, null on the last page. Max `limit` 200.

**[01:58] Priya Raman:** No offset pagination at all?

**[02:00] Raj Patel:** No. It falls over on big tables.

**[02:03] Raj Patel:** Summary: JSON/HTTPS, `snake_case`, plural paths, money as integer minor units plus ISO 4217, never floats, ISO 8601 UTC, prefixed IDs. Path versioning; breaking changes bump the version; old version supported at least 6 months; `Sunset` header. Standard error body; status code table as read. Cursor pagination, max limit 200.

**[02:24] (agreed)**

## Actions

- Raj — publish HTTP API guidelines.
- Marco — plan inventory `/v2` with `snake_case`.
