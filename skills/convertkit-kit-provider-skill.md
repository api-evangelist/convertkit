---
name: Kit
description: Use when building apps for the Kit App Store, creating plugins to extend Kit's UI, integrating with Kit's API for subscriber and email management, or helping developers understand Kit's authentication flows and best practices.
metadata:
    mintlify-proj: kit
    version: "1.0"
---

# Kit Developer Platform

## Product summary

Kit is an email-first operating system for creators. The Kit developer platform lets you build apps for the Kit App Store, create plugins that extend Kit's UI, or integrate with Kit's API to automate subscriber management, email campaigns, and creator workflows. 

**Key resources:**
- **API base URL:** `https://api.kit.com/v4/` (use `X-Kit-Api-Key` header for API keys or OAuth for apps)
- **App creation:** Visit `https://app.kit.com/apps?is=created` → "Build" tab → "+ New app"
- **Authentication:** OAuth 2.0 for published apps; API keys for personal testing only
- **Rate limits:** 600 requests/60s (OAuth) or 120 requests/60s (API keys)
- **Pagination:** Cursor-based with `after`/`before` query params; default 500 results, max 1000

**Primary docs:** https://developers.kit.com

## When to use

Reach for this skill when:
- **Building Kit apps:** Creating integrations for the Kit App Store (CRM, content distribution, AI tools, data analysis, audience building, task management)
- **Creating plugins:** Building content blocks (HTML elements in the email editor), media sources (external galleries), or automation nodes (custom workflow triggers/actions)
- **API integration:** Automating subscriber management, creating/sending broadcasts, managing tags/custom fields, syncing purchase data, or pulling email performance stats
- **Authentication setup:** Implementing OAuth flows for multi-creator apps or API key testing for personal automation
- **Troubleshooting:** Debugging rate limits, pagination issues, response codes, or plugin configuration problems

## Quick reference

### Authentication methods

| Method | Use case | Rate limit | Endpoints |
|--------|----------|-----------|-----------|
| OAuth 2.0 | Published apps, multi-creator | 600/60s | All (required for bulk/purchase) |
| API keys | Personal testing, single account | 120/60s | Most (not bulk/purchase) |

### Creating API keys

1. Go to account settings → "Developer" tab
2. Click "Add a new key" → name it → copy immediately (not retrievable later)
3. Use in requests: `curl -H 'X-Kit-Api-Key: YOUR_KEY' https://api.kit.com/v4/account`

### Common API endpoints

| Task | Endpoint | Method |
|------|----------|--------|
| List subscribers | `/v4/subscribers` | GET |
| Create subscriber | `/v4/subscribers` | POST |
| Tag subscriber | `/v4/tags/:tag_id/subscribers` | POST |
| List broadcasts | `/v4/broadcasts` | GET |
| Create broadcast | `/v4/broadcasts` | POST |
| List sequences | `/v4/sequences` | GET |
| Bulk create subscribers | `/v4/bulk/subscribers` | POST |
| Create webhook | `/v4/webhooks` | POST |

### Plugin types

| Type | Purpose | Auth | Use case |
|------|---------|------|----------|
| Content blocks | Custom HTML in email editor | OAuth or none | Product embeds, event promotions, dynamic content |
| Media source | External galleries in Kit | OAuth or none | GIPHY, stock photos, user-generated content |
| Automation nodes | Workflow triggers/actions | OAuth | Custom event listeners, external task execution |

### App submission checklist

- [ ] OAuth configured (if API access needed)
- [ ] App details page complete (icon, summary, description, resource links)
- [ ] Test credentials provided (if paid service)
- [ ] OAuth flows tested (not logged in, logged in, new signup, pre-loaded data)
- [ ] Meaningful use of Kit APIs/webhooks/plugins
- [ ] Support documentation provided
- [ ] No prohibited patterns (see Common gotchas)

## Decision guidance

### When to use API keys vs OAuth

| Scenario | Use API keys | Use OAuth |
|----------|-------------|----------|
| Testing endpoints personally | ✓ | |
| Building a published app | | ✓ |
| Multi-creator app | | ✓ |
| Bulk/purchase endpoints | | ✓ |
| Simple personal automation | ✓ | |

### When to build API app vs plugin vs both

| Approach | When to use |
|----------|------------|
| **API only** | Syncing external data (e.g., TeachKit syncing course subscribers) |
| **Plugin only** | Pulling public data (e.g., GIPHY images, no auth needed) |
| **Both** | Syncing subscribers + showing content in editor (e.g., Mighty Networks) |

### Pagination: cursor vs offset

Kit V4 uses **cursor-based pagination only**. Do not use page/offset parameters.

- Get first page: `GET /v4/subscribers`
- Get next page: `GET /v4/subscribers?after=END_CURSOR`
- Get previous page: `GET /v4/subscribers?before=START_CURSOR`
- Get total count: `GET /v4/subscribers?include_total_count=true` (slower)

## Workflow

### Building and publishing an app

1. **Create the app**
   - Go to `https://app.kit.com/apps?is=created` → "Build" tab
   - Click "+ New app" → enter name → save
   - Fill app details (icon, summary, description, resource links)

2. **Configure authentication**
   - Click "Authentication" tab
   - Choose: OAuth (for API access) or No auth (for public plugins)
   - If OAuth: set Authorization URL, Redirect URIs, Secure application toggle

3. **Build API or plugins**
   - **For API:** Use V4 endpoints; implement OAuth token refresh
   - **For plugins:** Create content blocks, media sources, or automation nodes with JSON configuration
   - Test with your own account before publishing

4. **Test thoroughly**
   - Install app in your own Kit account from the Build tab
   - Test all OAuth flows: logged out, logged in, new signup, pre-loaded data
   - Verify rate limiting handling (exponential backoff on 429)
   - Check error responses (422 for bad data, 401 for auth issues)

5. **Submit for review**
   - Complete pre-submission checklist (see Quick reference)
   - Click "Distribution" tab → "Submit for approval"
   - Email test credentials to apps@kit.com with functionality description
   - Kit reviews within 5 business days

6. **Publish**
   - Once approved, click "Publish" in Distribution tab
   - App appears in Kit App Store and marketing placements

### Implementing OAuth for an app

1. **Set up your OAuth server**
   - Create `/authorize` endpoint: redirect to Kit's OAuth server with `client_id`, `redirect_uri`, `state`
   - Create `/callback` endpoint: exchange authorization code for access/refresh tokens
   - Store refresh tokens securely; use them to request new access tokens when expired

2. **Configure in Kit**
   - App → Authentication tab
   - Set Authorization URL (your `/authorize` endpoint)
   - Set Redirect URIs (your `/callback` endpoint)
   - Toggle "Secure application" if using client secret

3. **Handle token refresh**
   - When access token expires, use refresh token to get new one
   - Implement exponential backoff for 429 rate limit responses

4. **Handle disconnection**
   - If creator uninstalls on your side: call `POST /v4/oauth/revoke` with access token
   - If creator uninstalls in Kit: Kit calls your revoke URL; clean up credentials

### Creating a content block plugin

1. **Set up authentication**
   - App → Authentication tab → choose OAuth or No auth

2. **Create the plugin**
   - Click "Plugins" tab → "+ New plugin"
   - Name it, select "Content blocks" type

3. **Configure the plugin**
   - **Name:** User-facing name (1-2 words, e.g., "Product")
   - **Description:** Short phrase (e.g., "Add a link to a product")
   - **Icon:** Monochrome SVG (150x120px recommended)
   - **Request URL:** Your endpoint that returns HTML
   - **Settings JSON:** Array of input fields (text, color, date, select, etc.)

4. **Implement the Request URL**
   - Receives POST with `settings` object (user's configured values)
   - Returns JSON: `{ "code": 200, "html": "<div>...</div>" }` or `{ "code": 404, "errors": ["error message"] }`

5. **Test and activate**
   - Install app in your account
   - Test plugin in email editor
   - Click "Active" toggle to make live for all users with app installed

## Common gotchas

- **API keys are not for published apps.** Use OAuth for any app going to the Kit App Store. API keys are personal testing only and have lower rate limits.

- **Some endpoints require OAuth.** Bulk operations (`/v4/bulk/`) and purchase creation require OAuth, not API keys. Check endpoint docs.

- **Cursor pagination is mandatory.** V3 used page/offset; V4 uses cursors only. Using `page` parameter will fail silently or return wrong results.

- **API key is shown once.** After leaving the Developer settings page, you cannot retrieve it again. Reset it to get a new one.

- **Plugins are live immediately.** Edits to active plugins take effect for all users instantly. Test changes on a new inactive plugin first, then swap.

- **OAuth token revocation is one-way.** When a creator uninstalls, call `POST /v4/oauth/revoke` to clean up Kit's side. Kit also calls your revoke URL to clean up your side.

- **Rate limits use rolling windows.** 600 requests over 60 seconds means requests are counted in a rolling 60-second window, not per-minute buckets. Use exponential backoff on 429 responses.

- **Bulk requests have size limits.** Max 300MB per app per creator account across all bulk requests. Requests exceeding this get 413 status.

- **Plugin authentication must be set before creating plugins.** If you try to create a plugin without choosing OAuth or No auth, you'll be prompted.

- **Apps must use Kit APIs meaningfully.** Apps that only export data or duplicate existing functionality will be rejected. Apps must enhance creator workflows.

- **Redirect URL after install requires allowlisted domains.** For security, domains must be pre-configured in app settings before using `return_to` parameter.

- **Test credentials are required for paid services.** If your app requires a paid account, provide test credentials or trial access for Kit's review team.

## Verification checklist

Before submitting an app for review:

- [ ] App uses OAuth (not API keys) for authentication
- [ ] All OAuth flows tested: logged out, logged in, new signup, pre-loaded data
- [ ] App details page complete with icon, summary, description, resource links
- [ ] Support documentation or help center article provided
- [ ] Rate limiting handled (exponential backoff on 429)
- [ ] Error responses handled (401, 422, 429, 500)
- [ ] Cursor-based pagination used (not page/offset)
- [ ] Plugins tested in editor before activation
- [ ] No prohibited patterns (data extraction only, duplicate functionality, spam automation)
- [ ] Test credentials provided (if applicable)
- [ ] Installation URL works with `k_app_id` parameter
- [ ] Redirect URL after install uses allowlisted domains (if applicable)

## Resources

**Comprehensive page listing:** https://developers.kit.com/llms.txt

**Critical documentation:**
- [API Reference Overview](https://developers.kit.com/api-reference/overview) — all endpoints, authentication, pagination, rate limits
- [Kit App Store Building Guide](https://developers.kit.com/kit-app-store/building-apps) — creating apps, OAuth setup, testing
- [Plugins Overview](https://developers.kit.com/plugins/overview) — content blocks, media sources, automation nodes

---

> For additional documentation and navigation, see: https://developers.kit.com/llms.txt