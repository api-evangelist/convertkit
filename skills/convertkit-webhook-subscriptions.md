---
name: Subscribe to Kit events with webhooks
description: Register, list and delete Kit webhooks across the 15 published event types, including the ones that require an entity id.
api: openapi/convertkit-webhooks-api-openapi.yml
operations:
- POST /v4/webhooks
- GET /v4/webhooks
- DELETE /v4/webhooks/{id}
provider: Kit
base_url: https://api.kit.com/v4
---

# Subscribe to Kit events with webhooks

Kit has **no AsyncAPI document** and **no webhook signing secret**. The event surface is the 15 types below,
one webhook registration per event.

## Register

`POST /v4/webhooks` with `target_url` and an `event` object. `event.name` is required; the id fields are
required *for the events that need them* and passed as `null` otherwise.

| Event | Required parameter |
|---|---|
| `subscriber.subscriber_activate` | — |
| `subscriber.subscriber_unsubscribe` | — |
| `subscriber.subscriber_bounce` | — |
| `subscriber.subscriber_complain` | — |
| `subscriber.form_subscribe` | `form_id` (integer) |
| `subscriber.course_subscribe` | `sequence_id` (integer) |
| `subscriber.course_complete` | `sequence_id` (integer) |
| `subscriber.link_click` | `initiator_value` (string — the link URL) |
| `subscriber.product_purchase` | `product_id` (integer) |
| `subscriber.tag_add` | `tag_id` (integer) |
| `subscriber.tag_remove` | `tag_id` (integer) |
| `purchase.purchase_create` | — |
| `custom_field.field_created` | — |
| `custom_field.field_deleted` | — |
| `custom_field.field_value_updated` | `custom_field_id` (integer) |

`course` is Kit's legacy name for a **sequence** — `subscriber.course_subscribe` fires on sequence entry.

## Manage

- `GET /v4/webhooks` — list the account's registrations.
- `DELETE /v4/webhooks/{id}` — remove one. There is no update; delete and re-create to change a target.

## Security warning

Kit publishes **no signature header, no signing secret, and no replay protection** for webhook deliveries.
Treat the payload as untrusted: use an unguessable `target_url` path, and re-fetch the referenced entity
through the API (`GET /v4/subscribers/{id}`, `GET /v4/purchases/{id}`) before acting on anything that
matters. Do not authorise a state change on the strength of the callback body alone.

## Not the same thing

`callback_url` on the `/v4/bulk/` endpoints is a **job-completion callback**, not a webhook subscription.
See `convertkit-bulk-import.md`.
