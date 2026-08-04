# Kit (ConvertKit)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Kit (formerly ConvertKit) is a creator email marketing platform with a REST API for managing subscribers, tags, sequences, forms, broadcasts, and automation rules.

- **Website:** https://kit.com
- **API Docs:** https://developers.kit.com
- **Status:** https://status.kit.com
- **Pricing:** https://kit.com/pricing
- **Changelog:** https://developers.kit.com/changelog
- **GitHub Org:** https://github.com/convertkit
- **LinkedIn:** https://www.linkedin.com/company/kit.com
- **X:** https://x.com/kit

## API

The Kit API v4 is a REST API with a base URL of `https://api.kit.com/v4`. It supports both API key authentication and OAuth 2.0.

### Authentication

- **API Key:** Pass via `X-Kit-Api-Key` header. Rate limit: 120 requests per 60-second rolling window.
- **OAuth 2.0:** Authorization Code Grant (with PKCE for SPAs/mobile). Rate limit: 600 requests per 60-second rolling window.

### Resources

- Subscribers
- Tags
- Sequences
- Forms
- Broadcasts
- Automation rules
- Custom fields
- Purchases (e-commerce, OAuth only)

## Plans

See [plans/convertkit-plans-pricing.yml](plans/convertkit-plans-pricing.yml) for full pricing details.

| Plan | Monthly Price | Subscribers |
|------|--------------|-------------|
| Newsletter | Free | Up to 10,000 |
| Creator | From $39/mo | From 1,000 (scales) |
| Pro | From $79/mo | From 1,000 (scales) |

All plans include API access.
