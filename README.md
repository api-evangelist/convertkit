# Kit

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Kit (formerly ConvertKit) is a creator email marketing platform whose REST API v4 covers subscribers, tags, custom fields, forms and landing pages, sequences, broadcasts, snippets, posts, purchases, segments and webhooks across 72 operations on https://api.kit.com/v4. It authenticates with an X-Kit-Api-Key header for personal automation or OAuth 2.0 (PKCE, dynamic client registration, rotating single-use refresh tokens) for apps published to the Kit App Store, and uses cursor-based pagination, an OAuth-only bulk namespace with async callbacks, and eventually-consistent list reads. Kit also runs two remote MCP servers - an OAuth-gated one that acts on a creator's account and an anonymous read-only documentation server - publishes an A2A agent card and an Agent Skill from its developer docs host, and ships llms.txt. Its only first-party API client is a PHP SDK.

**Areas:** Email Marketing · Creator Economy · Subscribers · Automation · Newsletters · Sequences · Forms · Broadcast · Webhook · MCP · Agents · Authentication

## Kit on APIs.io

Everything profiled for Kit is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/convertkit/](https://apis.io/providers/convertkit/)** — or go straight to one of the APIs or properties below.

### APIs (16)

- [Kit Accounts API](https://apis.io/apis/convertkit/convertkit-accounts-api/) — The Accounts API from Kit — 5 operation(s) for accounts.
- [Kit Broadcasts API](https://apis.io/apis/convertkit/convertkit-broadcasts-api/) — The Broadcasts API from Kit — 5 operation(s) for broadcasts.
- [Kit Custom Fields API](https://apis.io/apis/convertkit/convertkit-custom-fields-api/) — The Custom Fields API from Kit — 4 operation(s) for custom fields.
- [Kit Email Templates API](https://apis.io/apis/convertkit/convertkit-email-templates-api/) — The Email Templates API from Kit — 1 operation(s) for email templates.
- [Kit Forms API](https://apis.io/apis/convertkit/convertkit-forms-api/) — The Forms API from Kit — 4 operation(s) for forms.
- [Kit Posts API](https://apis.io/apis/convertkit/convertkit-posts-api/) — The Posts API from Kit — 2 operation(s) for posts.
- [Kit Purchases API](https://apis.io/apis/convertkit/convertkit-purchases-api/) — The Purchases API from Kit — 2 operation(s) for purchases.
- [Kit Segments API](https://apis.io/apis/convertkit/convertkit-segments-api/) — The Segments API from Kit — 1 operation(s) for segments.
- [Kit Sequence Emails API](https://apis.io/apis/convertkit/convertkit-sequence-emails-api/) — The Sequence Emails API from Kit — 2 operation(s) for sequence emails.
- [Kit Sequences API](https://apis.io/apis/convertkit/convertkit-sequences-api/) — The Sequences API from Kit — 4 operation(s) for sequences.
- [Kit Snippets API](https://apis.io/apis/convertkit/convertkit-snippets-api/) — The Snippets API from Kit — 2 operation(s) for snippets.
- [Kit Subscribers API](https://apis.io/apis/convertkit/convertkit-subscribers-api/) — The Subscribers API from Kit — 7 operation(s) for subscribers.
- [Kit Tags API](https://apis.io/apis/convertkit/convertkit-tags-api/) — The Tags API from Kit — 6 operation(s) for tags.
- [Kit Webhooks API](https://apis.io/apis/convertkit/convertkit-webhooks-api/) — The Webhooks API from Kit — 2 operation(s) for webhooks.
- [Kit API V3 (Deprecated)](https://apis.io/apis/convertkit/kit-api-v3/) — The legacy ConvertKit V3 API is deprecated and slated for discontinuation; new integrations should target V4.
- [Kit Account API](https://apis.io/apis/convertkit/convertkit-account-api/) — Account, creator profile, and account-level statistics

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (2)

Event-driven and webhook contracts.

- [Convertkit Webhooks](https://apis.io/asyncapis/convertkit/convertkit-webhooks/)
- [Kit Webhooks](https://apis.io/asyncapis/convertkit/kit-webhooks-asyncapi/)

#### Event channels (15)

Individual events and webhooks the provider emits.

- [custom_field.field_created](https://apis.io/channels/convertkit/custom-field-field-created/)
- [custom_field.field_deleted](https://apis.io/channels/convertkit/custom-field-field-deleted/)
- [custom_field.field_value_updated](https://apis.io/channels/convertkit/custom-field-field-value-updated/)
- [purchase.purchase_create](https://apis.io/channels/convertkit/purchase-purchase-create/)
- [subscriber.course_complete](https://apis.io/channels/convertkit/subscriber-course-complete/)
- [subscriber.course_subscribe](https://apis.io/channels/convertkit/subscriber-course-subscribe/)
- [subscriber.form_subscribe](https://apis.io/channels/convertkit/subscriber-form-subscribe/)
- [subscriber.link_click](https://apis.io/channels/convertkit/subscriber-link-click/)
- [subscriber.product_purchase](https://apis.io/channels/convertkit/subscriber-product-purchase/)
- [subscriber.subscriber_activate](https://apis.io/channels/convertkit/subscriber-subscriber-activate/)
- [subscriber.subscriber_bounce](https://apis.io/channels/convertkit/subscriber-subscriber-bounce/)
- [subscriber.subscriber_complain](https://apis.io/channels/convertkit/subscriber-subscriber-complain/)
- [subscriber.subscriber_unsubscribe](https://apis.io/channels/convertkit/subscriber-subscriber-unsubscribe/)
- [subscriber.tag_add](https://apis.io/channels/convertkit/subscriber-tag-add/)
- [subscriber.tag_remove](https://apis.io/channels/convertkit/subscriber-tag-remove/)

#### GraphQL (1)

GraphQL schemas.

- [Moved to /providers/convertkit/](https://apis.io/graphqls/convertkit/convertkit-graphql/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [convertkit-mcp.yml](https://apis.io/servers/convertkit/convertkit-mcp-yml/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Convertkit Agentic Access](https://apis.io/agentic-access/convertkit/convertkit-agentic-access/)

#### JSON Schema (105)

The data models the API reads and writes.

- [BroadcastAnyCondition](https://apis.io/schemas/convertkit/BroadcastAnyCondition/)
- [FilterCondition](https://apis.io/schemas/convertkit/FilterCondition/)
- [FormsAnyCondition](https://apis.io/schemas/convertkit/FormsAnyCondition/)
- [IdsAnyCondition](https://apis.io/schemas/convertkit/IdsAnyCondition/)
- [SubscriberFilterRequest](https://apis.io/schemas/convertkit/SubscriberFilterRequest/)
- [UrlAnyCondition](https://apis.io/schemas/convertkit/UrlAnyCondition/)
- [Add subscriber to form by email address Request](https://apis.io/schemas/convertkit/add_subscriber_to_form_by_email_address_request/)
- [Add subscriber to form by email address Response](https://apis.io/schemas/convertkit/add_subscriber_to_form_by_email_address_response/)
- [Add subscriber to form Request](https://apis.io/schemas/convertkit/add_subscriber_to_form_request/)
- [Add subscriber to form Response](https://apis.io/schemas/convertkit/add_subscriber_to_form_response/)
- [Add subscriber to sequence by email address Request](https://apis.io/schemas/convertkit/add_subscriber_to_sequence_by_email_address_request/)
- [Add subscriber to sequence by email address Response](https://apis.io/schemas/convertkit/add_subscriber_to_sequence_by_email_address_response/)
- [Add subscriber to sequence Request](https://apis.io/schemas/convertkit/add_subscriber_to_sequence_request/)
- [Add subscriber to sequence Response](https://apis.io/schemas/convertkit/add_subscriber_to_sequence_response/)
- [Bulk add subscribers to forms Request](https://apis.io/schemas/convertkit/bulk_add_subscribers_to_forms_request/)
- [Bulk add subscribers to forms Response](https://apis.io/schemas/convertkit/bulk_add_subscribers_to_forms_response/)
- [Bulk create custom fields Request](https://apis.io/schemas/convertkit/bulk_create_custom_fields_request/)
- [Bulk create custom fields Response](https://apis.io/schemas/convertkit/bulk_create_custom_fields_response/)
- [Bulk create subscribers Request](https://apis.io/schemas/convertkit/bulk_create_subscribers_request/)
- [Bulk create subscribers Response](https://apis.io/schemas/convertkit/bulk_create_subscribers_response/)
- [Bulk create tags Request](https://apis.io/schemas/convertkit/bulk_create_tags_request/)
- [Bulk create tags Response](https://apis.io/schemas/convertkit/bulk_create_tags_response/)
- [Bulk remove tags from subscribers Response](https://apis.io/schemas/convertkit/bulk_remove_tags_from_subscribers_response/)
- [Bulk tag subscribers Request](https://apis.io/schemas/convertkit/bulk_tag_subscribers_request/)
- [Bulk tag subscribers Response](https://apis.io/schemas/convertkit/bulk_tag_subscribers_response/)
- …and 80 more published on APIs.io

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Convertkit Context](https://apis.io/jsonld/convertkit/convertkit-context/)

#### Examples (72)

Example requests and responses.

- [Add Subscriber To Form](https://apis.io/examples/convertkit/add-subscriber-to-form/)
- [Add Subscriber To Form By Email Address](https://apis.io/examples/convertkit/add-subscriber-to-form-by-email-address/)
- [Add Subscriber To Sequence](https://apis.io/examples/convertkit/add-subscriber-to-sequence/)
- [Add Subscriber To Sequence By Email Address](https://apis.io/examples/convertkit/add-subscriber-to-sequence-by-email-address/)
- [Bulk Add Subscribers To Forms](https://apis.io/examples/convertkit/bulk-add-subscribers-to-forms/)
- [Bulk Create Custom Fields](https://apis.io/examples/convertkit/bulk-create-custom-fields/)
- [Bulk Create Subscribers](https://apis.io/examples/convertkit/bulk-create-subscribers/)
- [Bulk Create Tags](https://apis.io/examples/convertkit/bulk-create-tags/)
- [Bulk Remove Tags From Subscribers](https://apis.io/examples/convertkit/bulk-remove-tags-from-subscribers/)
- [Bulk Tag Subscribers](https://apis.io/examples/convertkit/bulk-tag-subscribers/)
- [Bulk Update Subscriber Custom Field Values](https://apis.io/examples/convertkit/bulk-update-subscriber-custom-field-values/)
- [Create A Broadcast](https://apis.io/examples/convertkit/create-a-broadcast/)
- [Create A Custom Field](https://apis.io/examples/convertkit/create-a-custom-field/)
- [Create A Purchase](https://apis.io/examples/convertkit/create-a-purchase/)
- [Create A Sequence](https://apis.io/examples/convertkit/create-a-sequence/)
- [Create A Sequence Email](https://apis.io/examples/convertkit/create-a-sequence-email/)
- [Create A Snippet](https://apis.io/examples/convertkit/create-a-snippet/)
- [Create A Subscriber](https://apis.io/examples/convertkit/create-a-subscriber/)
- [Create A Tag](https://apis.io/examples/convertkit/create-a-tag/)
- [Create A Webhook](https://apis.io/examples/convertkit/create-a-webhook/)
- [Delete A Broadcast](https://apis.io/examples/convertkit/delete-a-broadcast/)
- [Delete A Sequence](https://apis.io/examples/convertkit/delete-a-sequence/)
- [Delete A Sequence Email](https://apis.io/examples/convertkit/delete-a-sequence-email/)
- [Delete A Webhook](https://apis.io/examples/convertkit/delete-a-webhook/)
- [Delete Custom Field](https://apis.io/examples/convertkit/delete-custom-field/)
- …and 47 more published on APIs.io

#### Collections (14)

Postman and Open Collection request collections.

- [Kit Accounts API](https://apis.io/collections/convertkit/open-convertkit-accounts-api/)
- [Kit Accounts Broadcasts API](https://apis.io/collections/convertkit/open-convertkit-broadcasts-api/)
- [Kit Accounts Custom Fields API](https://apis.io/collections/convertkit/open-convertkit-custom-fields-api/)
- [Kit Accounts Email Templates API](https://apis.io/collections/convertkit/open-convertkit-email-templates-api/)
- [Kit Accounts Forms API](https://apis.io/collections/convertkit/open-convertkit-forms-api/)
- [Kit Accounts Posts API](https://apis.io/collections/convertkit/open-convertkit-posts-api/)
- [Kit Accounts Purchases API](https://apis.io/collections/convertkit/open-convertkit-purchases-api/)
- [Kit Accounts Segments API](https://apis.io/collections/convertkit/open-convertkit-segments-api/)
- [Kit Accounts Sequence Emails API](https://apis.io/collections/convertkit/open-convertkit-sequence-emails-api/)
- [Kit Accounts Sequences API](https://apis.io/collections/convertkit/open-convertkit-sequences-api/)
- [Kit Accounts Snippets API](https://apis.io/collections/convertkit/open-convertkit-snippets-api/)
- [Kit Accounts Subscribers API](https://apis.io/collections/convertkit/open-convertkit-subscribers-api/)
- [Kit Accounts Tags API](https://apis.io/collections/convertkit/open-convertkit-tags-api/)
- [Kit Accounts Webhooks API](https://apis.io/collections/convertkit/open-convertkit-webhooks-api/)

#### Overlays (29)

OpenAPI overlays, including conversational phrasing for each operation.

- [Convertkit Account Api Phrasing Overlay](https://apis.io/overlays/convertkit/convertkit-account-api-phrasing-overlay/)
- [Convertkit Accounts Api Phrasing Overlay](https://apis.io/overlays/convertkit/convertkit-accounts-api-phrasing-overlay/)
- [Convertkit Accounts Overlay](https://apis.io/overlays/convertkit/convertkit-accounts-overlay/)
- [Convertkit Broadcasts Api Phrasing Overlay](https://apis.io/overlays/convertkit/convertkit-broadcasts-api-phrasing-overlay/)
- [Convertkit Broadcasts Overlay](https://apis.io/overlays/convertkit/convertkit-broadcasts-overlay/)
- [Convertkit Custom Fields Api Phrasing Overlay](https://apis.io/overlays/convertkit/convertkit-custom-fields-api-phrasing-overlay/)
- [Convertkit Custom Fields Overlay](https://apis.io/overlays/convertkit/convertkit-custom-fields-overlay/)
- [Convertkit Email Templates Api Phrasing Overlay](https://apis.io/overlays/convertkit/convertkit-email-templates-api-phrasing-overlay/)
- [Convertkit Email Templates Overlay](https://apis.io/overlays/convertkit/convertkit-email-templates-overlay/)
- [Convertkit Forms Api Phrasing Overlay](https://apis.io/overlays/convertkit/convertkit-forms-api-phrasing-overlay/)
- [Convertkit Forms Overlay](https://apis.io/overlays/convertkit/convertkit-forms-overlay/)
- [Convertkit Posts Api Phrasing Overlay](https://apis.io/overlays/convertkit/convertkit-posts-api-phrasing-overlay/)
- [Convertkit Posts Overlay](https://apis.io/overlays/convertkit/convertkit-posts-overlay/)
- [Convertkit Purchases Api Phrasing Overlay](https://apis.io/overlays/convertkit/convertkit-purchases-api-phrasing-overlay/)
- [Convertkit Purchases Overlay](https://apis.io/overlays/convertkit/convertkit-purchases-overlay/)
- [Convertkit Segments Api Phrasing Overlay](https://apis.io/overlays/convertkit/convertkit-segments-api-phrasing-overlay/)
- [Convertkit Segments Overlay](https://apis.io/overlays/convertkit/convertkit-segments-overlay/)
- [Convertkit Sequence Emails Api Phrasing Overlay](https://apis.io/overlays/convertkit/convertkit-sequence-emails-api-phrasing-overlay/)
- [Convertkit Sequence Emails Overlay](https://apis.io/overlays/convertkit/convertkit-sequence-emails-overlay/)
- [Convertkit Sequences Api Phrasing Overlay](https://apis.io/overlays/convertkit/convertkit-sequences-api-phrasing-overlay/)
- [Convertkit Sequences Overlay](https://apis.io/overlays/convertkit/convertkit-sequences-overlay/)
- [Convertkit Snippets Api Phrasing Overlay](https://apis.io/overlays/convertkit/convertkit-snippets-api-phrasing-overlay/)
- [Convertkit Snippets Overlay](https://apis.io/overlays/convertkit/convertkit-snippets-overlay/)
- [Convertkit Subscribers Api Phrasing Overlay](https://apis.io/overlays/convertkit/convertkit-subscribers-api-phrasing-overlay/)
- [Convertkit Subscribers Overlay](https://apis.io/overlays/convertkit/convertkit-subscribers-overlay/)
- …and 4 more published on APIs.io

#### Governance rules (2)

Spectral rulesets for the provider's contracts.

- [Kit — jsonschema rules](https://apis.io/rules/convertkit/convertkit-jsonschema-spectral-rules/)
- [Kit API Rules](https://apis.io/rules/convertkit/convertkit-rules/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Convertkit Authentication](https://apis.io/security/convertkit/convertkit-authentication/)
- [Convertkit Domain Security](https://apis.io/security/convertkit/convertkit-domain-security/)
- [Convertkit Trust Center](https://apis.io/security/convertkit/convertkit-trust-center/)
- [Convertkit Vulnerability Disclosure](https://apis.io/security/convertkit/convertkit-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Convertkit Scopes](https://apis.io/scopes/convertkit/convertkit-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Convertkit Plans Pricing](https://apis.io/plans/convertkit/convertkit-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Convertkit Rate Limits](https://apis.io/rate-limits/convertkit/convertkit-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Convertkit Finops](https://apis.io/finops/convertkit/convertkit-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://kit.com)
- [Documentation](https://developers.kit.com)
- [Getting started](https://developers.kit.com/kit-app-store/quick-start-guide)
- [API reference](https://developers.kit.com/api-reference/overview)
- [Pricing](https://kit.com/pricing)
- [Sign up](https://app.kit.com/users/signup)
- [Support](https://kit.com/support)
- [Blog](https://kit.com/resources)
- [Security](https://kit.com/security)
- [Compliance](https://kit.com/security)
- [Terms of service](https://kit.com/terms)
- [Privacy policy](https://kit.com/privacy)
- [GitHub](https://github.com/Kit)
- [Status](https://status.kit.com)

## API Evangelist rating

**Kin Score 79.7** — exemplar · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 76.7 |
| Contract quality | 76.4 |
| Contract governance | 35.6 |
| Operational transparency | 92.1 |
| Developer ergonomics | 71.4 |
| Access clarity | 92.1 |

**Agent readiness 64.4** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | verified |
| Auth Clarity | served (partial credit) |
| Idempotency | documented (partial credit) |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | yes |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 44.2** — Telecommunications

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/convertkit/](https://apis.io/providers/convertkit/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Kit: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/convertkit/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
