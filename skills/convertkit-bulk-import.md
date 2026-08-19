---
name: Bulk import subscribers and tags into Kit
description: Use Kit's OAuth-only bulk namespace with async callbacks to load subscribers, tags, and custom field values at volume without tripping the 413 queue limit.
api: openapi/convertkit-subscribers-api-openapi.yml
operations:
- POST /v4/bulk/subscribers
- POST /v4/bulk/tags
- DELETE /v4/bulk/tags
- POST /v4/bulk/tags/subscribers
- DELETE /v4/bulk/tags/subscribers
- POST /v4/bulk/custom_fields
- POST /v4/bulk/custom_fields/subscribers
- POST /v4/bulk/forms/subscribers
provider: Kit
base_url: https://api.kit.com/v4
---

# Bulk import subscribers and tags into Kit

## Hard requirements

- **OAuth only.** Every operation under `/v4/bulk/` rejects `X-Kit-Api-Key`. You need an OAuth access token.
  This is the single most common cause of a `401` on a bulk call.
- **300MB budget.** Kit accepts up to 300MB of request data per app, per creator account, **shared across
  every bulk endpoint**. Exceeding it returns `413`.

## Steps

1. **Create the custom fields first.** `POST /v4/bulk/custom_fields`. Values cannot be set against keys
   that do not exist yet.
2. **Create the tags first.** `POST /v4/bulk/tags`. Tag creation is idempotent on name (case-insensitive),
   so re-running this is safe.
3. **Load the subscribers.** `POST /v4/bulk/subscribers`. Small batches process synchronously and return
   `200`; the cut-off is documented per endpoint. For large batches, include a **`callback_url`** in the
   request body — Kit `POST`s to it on completion with the same body shape as the synchronous `200 OK`
   response, and the immediate response is `202 Accepted`.
4. **Attach values and tags.** `POST /v4/bulk/custom_fields/subscribers` pairs each `subscriber_id` with a
   `subscriber_custom_field_id` and a `value`. `POST /v4/bulk/tags/subscribers` tags subscribers that
   **already exist** — create them in step 3 first.
5. **Add to forms.** `POST /v4/bulk/forms/subscribers`. Adding subscribers to a **double opt-in** form
   triggers an Incentive Email; subscribers already on that form are not re-sent it.

## The mistake to avoid

**Do not poll a list endpoint to confirm the import landed.** Bulk jobs run asynchronously *and* Kit's
list/filter reads are eventually consistent (p50 ~30s, p99 up to 5 minutes), so the two delays compound.
A `202 Accepted` means the work is queued. Use the `callback_url` instead of polling. If you must poll,
use exponential backoff — start at 250–500ms, cap at 5s, give up after 30–60s.

## Errors

- `413` — too much enqueued. Drain the queue, wait, retry.
- `401` — almost always an API key on an OAuth-only endpoint.
- `422` — a field in the batch is bad or missing; the `errors[]` array names it. Deterministic; fix and resend.
