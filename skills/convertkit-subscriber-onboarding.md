---
name: Onboard a subscriber into Kit
description: Create or upsert a subscriber, apply tags, set custom field values, and enrol them in a sequence — the core Kit list-building flow.
api: openapi/convertkit-subscribers-api-openapi.yml
operations:
- POST /v4/subscribers
- GET /v4/custom_fields
- POST /v4/custom_fields
- POST /v4/tags
- POST /v4/tags/{tag_id}/subscribers
- POST /v4/sequences/{sequence_id}/subscribers
- GET /v4/subscribers/{id}
provider: Kit
base_url: https://api.kit.com/v4
---

# Onboard a subscriber into Kit

> Kit's OpenAPI declares no `operationId` on any of its 72 operations. Every step below is grounded in the
> METHOD + path that the published spec actually contains — verify against `openapi/_original/openapi.json`.

## Before you start

- **Auth.** Send `X-Kit-Api-Key: <key>` for personal automation, or an OAuth bearer token for a published app.
  OAuth is required for anything under `/v4/bulk/` and for `POST /v4/purchases`.
- **Rate limit.** 600 req / rolling 60s on OAuth, 120 req / rolling 60s on an API key. On `429` there is
  **no `Retry-After` header** — back off exponentially on your side.
- **No idempotency key.** Kit publishes no `Idempotency-Key` contract. Do not blind-retry writes.
  Two operations are naturally safe: `POST /v4/subscribers` upserts on email address, and `POST /v4/tags`
  is idempotent on name (returns `200` + the existing tag, `201` on a real create).

## Steps

1. **Ensure the custom fields exist.** `GET /v4/custom_fields` and check the `key` values you intend to set.
   Sending an unknown custom field key on a subscriber write returns an error — it does not auto-create.
   Create missing ones with `POST /v4/custom_fields` (supply `label`; Kit derives `key` and `name`).
2. **Create or update the subscriber.** `POST /v4/subscribers` with `email_address`, `first_name`, optional
   `state`, and a `fields` object keyed by custom field `key`. This is an upsert — an existing email address
   is updated, not rejected. **Keep the `id` from the response.**
3. **Ensure the tag exists.** `POST /v4/tags` with `name`. A `200` means the tag already existed; a `201`
   means you just created it. Either way the response carries the `id`.
4. **Apply the tag.** `POST /v4/tags/{tag_id}/subscribers/{id}` using the two ids you now hold, or
   `POST /v4/tags/{tag_id}/subscribers` with `email_address` if you only have the address.
5. **Enrol in a sequence (optional).** `POST /v4/sequences/{sequence_id}/subscribers/{id}`.
   Get `sequence_id` from `GET /v4/sequences`.
6. **Do not read back to confirm.** `GET /v4/subscribers` and every filter endpoint are **eventually
   consistent** — p50 ~30s, p99 up to 5 minutes. Trust the write response. If you must verify, use the
   strongly-consistent direct lookup `GET /v4/subscribers/{id}` with the id from step 2.

## Error handling

| Status | Meaning | Do |
|---|---|---|
| 401 | Bad/missing credential, wrong auth method for the endpoint, or the account lost API access | Read `errors[0]`; do not retry unchanged |
| 403 | Authenticated but not entitled | Check plan/app grants |
| 404 | Resource absent — but a just-created resource can 404 on a list read for up to 5 min | Use the id-based lookup |
| 422 | Bad or missing field | Fix the field named in `errors[]`; deterministic, do not retry |
| 429 | Rate limited | Exponential backoff, client-side |

Errors always arrive as `{"errors": ["message", ...]}` — an array of human-readable strings with **no
machine-readable code**. Branch on the HTTP status, not the string.
