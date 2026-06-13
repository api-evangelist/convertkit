# Kit (ConvertKit)

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
