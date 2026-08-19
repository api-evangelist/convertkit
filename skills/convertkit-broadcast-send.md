---
name: Draft, target and send a Kit broadcast
description: Compose a broadcast against an email template, target it with a subscriber filter, schedule the send, and read back delivery and click performance.
api: openapi/convertkit-broadcasts-api-openapi.yml
operations:
- GET /v4/email_templates
- POST /v4/subscribers/filter
- POST /v4/broadcasts
- PUT /v4/broadcasts/{id}
- GET /v4/broadcasts/{id}
- GET /v4/broadcasts/{broadcast_id}/stats
- GET /v4/broadcasts/{broadcast_id}/clicks
- DELETE /v4/broadcasts/{id}
provider: Kit
base_url: https://api.kit.com/v4
---

# Draft, target and send a Kit broadcast

> Sending a broadcast is **destructive and irreversible** — it puts email in front of real subscribers.
> Kit's own MCP marks send/delete tools with `destructiveHint` and requires explicit user confirmation.
> An agent must do the same: confirm with the human before any call that transitions a broadcast to sending.

## Steps

1. **Pick the template.** `GET /v4/email_templates` and take the `id` of the template you want.
   V4 removed V3's `email_layout_template` string — you must pass `email_template_id`.
2. **Work out the audience (optional).** `POST /v4/subscribers/filter` to test a compound condition —
   engagement (opens/clicks/sends/deliveries with count thresholds and date ranges), sign-up date,
   `subscriber_state`, `tags`, `custom_field`, `location`, attribution. Every condition in the `all` array
   must match (AND logic). Add `include: ["stats"]` to see engagement alongside each match.
3. **Save a draft.** `POST /v4/broadcasts` with `subject`, `content` (HTML), `email_template_id`,
   optional `subscriber_filter`, and **`send_at: null`**. `null` is what makes it a draft.
   Set `public: true` to also publish it to the web.
4. **Review.** `GET /v4/broadcasts/{id}` returns the full record including `status`
   (`draft`, `scheduled`, `sending`, `completed`, `aborted`) and `public_url`.
5. **Schedule the send — CONFIRM FIRST.** `PUT /v4/broadcasts/{id}` with a `send_at` timestamp
   (ISO 8601 UTC). A scheduled broadcast must contain subject and content.
6. **Measure.** `GET /v4/broadcasts/{broadcast_id}/stats` for recipients / opens / clicks / unsubscribes
   and their rates plus `status` and `progress`. `GET /v4/broadcasts/{broadcast_id}/clicks` for per-link
   `unique_clicks` and click-to-delivery / click-to-open rates. For many broadcasts at once use
   `GET /v4/broadcasts/stats` — one request instead of one per broadcast.

## Rules

- `DELETE /v4/broadcasts/{id}` is a **hard delete** of a draft or scheduled broadcast, returns `204`,
  and cannot be undone. Only draft/scheduled broadcasts can be deleted.
- `?status=` on `GET /v4/broadcasts` and `GET /v4/broadcasts/stats` filters by lifecycle state; an unknown
  value returns `422` listing the accepted values.
- Broadcast list endpoints are cursor-paginated (`after`/`before`/`per_page`, default 500, max 1000) and
  accept `?slim=true` to skip the custom-field join.
- `open_tracking_disabled` / `click_tracking_disabled` on the stats response tell you whether the numbers
  are meaningful at all. Check them before reporting a 0% open rate as a result.
