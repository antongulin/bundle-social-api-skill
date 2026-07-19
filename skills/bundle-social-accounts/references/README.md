# Bundle.social API Documentation

**Base URL:** `https://api.bundle.social`
**API Version:** 1.0.0
**OpenAPI:** 3.0.2

## Authentication

All endpoints require authentication via the `x-api-key` header.

## Supported Platforms

| Platform | Enum Value |
|----------|-----------|
| Facebook | `FACEBOOK` |
| Instagram | `INSTAGRAM` |
| TikTok | `TIKTOK` |
| YouTube | `YOUTUBE` |
| Twitter/X | `TWITTER` |
| Pinterest | `PINTEREST` |
| Reddit | `REDDIT` |
| Mastodon | `MASTODON` |
| Discord | `DISCORD` |
| Slack | `SLACK` |
| Bluesky | `BLUESKY` |
| Google Business | `GOOGLE_BUSINESS` |
| LinkedIn | `LINKEDIN` |
| Threads | `THREADS` |

## Standard Error Responses

All endpoints share these common error responses:

| Status | Description |
|--------|-------------|
| `400` | Validation error - includes Zod validation `issues` array |
| `401` | Unauthorized - missing or invalid API key |
| `403` | Forbidden - insufficient permissions |
| `404` | Resource not found |
| `429` | Rate limited |
| `500` | Internal server error |

Error body format:
```json
{
  "statusCode": 400,
  "message": "Validation error",
  "issues": [
    { "code": "invalid_type", "message": "Expected string, received number", "path": ["fieldName"] }
  ]
}
```

## Endpoints Index

| # | Tag | Count | File |
|---|-----|-------|------|
| 4 | `socialAccount` | 11 | [04-social-account.md](./04-social-account.md) |

**Included: 11 endpoints**

See the [complete API index](../../../docs/api/README.md) for all 111 endpoints.
