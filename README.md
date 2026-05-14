# Bundle.social API Skills

[![skills.sh](https://skills.sh/b/antongulin/bundle-social-api-skill)](https://skills.sh/antongulin/bundle-social-api-skill)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](LICENSE)

AI agent skills for the [Bundle.social API](https://api.bundle.social) — social media management platform supporting 14 platforms.

> **Author**: Anton Gulin · **Tool**: [opencode-skill-creator](https://github.com/antongulin/opencode-skill-creator) · **GitHub**: [@antongulin](https://github.com/antongulin) · **Registry**: [skills.sh](https://www.skills.sh/docs)

Skills package providing AI coding assistants with structured instructions for helping users manage social media content, accounts, analytics, and platform-specific operations through the Bundle.social API.

## Skills

### [bundle-social-core](/skills/bundle-social-core)

Manage organizations, teams, and API health checks. Covers org details, usage limits, team CRUD, and platform status monitoring.

```bash
curl https://api.bundle.social/api/v1/ \
  -H "x-api-key: <your-api-key>"
```

### [bundle-social-accounts](/skills/bundle-social-accounts)

Connect, disconnect, and manage social accounts across 14 platforms. OAuth connection flow, channel setup (Discord, Slack, Reddit), portal links, connection checks, and profile refreshes.

```bash
curl -X POST https://api.bundle.social/api/v1/social-account/connect \
  -H "x-api-key: <your-api-key>" \
  -H "Content-Type: application/json" \
  -d '{"type": "INSTAGRAM", "teamId": "team_123", "redirectUrl": "https://myapp.com/callback"}'
```

### [bundle-social-posts](/skills/bundle-social-posts)

Full post lifecycle: create, read, update, delete, and retry publishing. Multi-platform content blocks, scheduling, status tracking.

```bash
curl -X POST https://api.bundle.social/api/v1/post/ \
  -H "x-api-key: <your-api-key>" \
  -H "Content-Type: application/json" \
  -d '{"teamId": "team_123", "title": "Hello World", "platforms": {"INSTAGRAM": {"text": "Hello!"}}}'
```

### [bundle-social-comments](/skills/bundle-social-comments)

Read, create, update, delete comments and import comment threads from Facebook, Instagram, LinkedIn, YouTube, TikTok, Reddit, and more.

```bash
curl https://api.bundle.social/api/v1/comment/?teamId=team_123&postId=post_456 \
  -H "x-api-key: <your-api-key>"
```

### [bundle-social-analytics](/skills/bundle-social-analytics)

Retrieve performance metrics for social accounts and posts. Impressions, views, likes, shares, engagement rates, follower counts. Supports date-range filtering, granularity, and bulk post comparison.

```bash
curl "https://api.bundle.social/api/v1/analytics/social-account?socialAccountId=acc_123&teamId=team_123&dateFrom=2026-01-01&dateTo=2026-05-13" \
  -H "x-api-key: <your-api-key>"
```

### [bundle-social-uploads](/skills/bundle-social-uploads)

Upload media files via direct upload, URL import, or multipart for large files. List, search, and bulk-delete uploads.

```bash
curl -X POST https://api.bundle.social/api/v1/upload/ \
  -H "x-api-key: <your-api-key>" \
  -F "file=@/path/to/image.jpg"
```

### [bundle-social-platform-ops](/skills/bundle-social-platform-ops)

Platform-specific operations across 13 platforms: YouTube playlists, Google Business Profile management, LinkedIn mentions, Reddit flairs, Facebook recommendations, TikTok music, and more (48 endpoints).

```bash
curl -X POST https://api.bundle.social/api/v1/misc/youtube/playlist \
  -H "x-api-key: <your-api-key>" \
  -H "Content-Type: application/json" \
  -d '{"teamId": "team_123", "title": "My Playlist", "privacyStatus": "PUBLIC"}'
```

### [bundle-social-import](/skills/bundle-social-import)

Import historical post data from connected accounts and bulk-create posts via CSV upload. Full workflow: start import → monitor status → retrieve results.

```bash
curl -X POST https://api.bundle.social/api/v1/post-history-import/ \
  -H "x-api-key: <your-api-key>" \
  -H "Content-Type: application/json" \
  -d '{"teamId": "team_123", "socialAccountId": "acc_123", "importAnalytics": true}'
```

## Installation

### Using the Skills CLI (recommended)

**Project scope** — installs locally in the current project:

```bash
npx skills add antongulin/bundle-social-api-skill
```

**Global scope** (`-g`) — available across all projects:

```bash
npx skills add antongulin/bundle-social-api-skill -g
```

The CLI automatically detects your installed coding agents. See [skills.sh](https://skills.sh) for more options.

### Manual

Clone the repo and copy the skills to your agent's skills path:

```bash
git clone https://github.com/antongulin/bundle-social-api-skill.git
cp -r bundle-social-api-skill/.opencode/skills/* <agent-skills-path>/
```

Replace `<agent-skills-path>` with your agent's skills directory. Common paths:

| Agent | Path |
|-------|------|
| Universal | `~/.agents/skills/` |
| OpenCode | `~/.config/opencode/skills/` |
| Claude Code | `~/.claude/skills/` |
| GitHub Copilot | `~/.copilot/skills/` |
| Cursor | `~/.cursor/skills/` |
| Gemini CLI | `~/.gemini/skills/` |
| Cline | `~/.agents/skills/` |
| Codex | `~/.codex/skills/` |

## API Overview

The Bundle.social API is a RESTful API at `https://api.bundle.social` with 111 endpoints across 11 categories.

**Authentication:** All endpoints require the `x-api-key` header.

**Supported platforms:** Facebook, Instagram, TikTok, YouTube, Twitter/X, Pinterest, Reddit, Mastodon, Discord, Slack, Bluesky, Google Business, LinkedIn, Threads.

## Compatibility

Skills are compatible with AI coding assistants that support the [skills.sh](https://www.skills.sh/docs) skill format, including OpenCode, Claude Code, Copilot CLI, Cursor, Codex, Cline, Gemini CLI, and 50+ others.

## Related

- [Bundle.social](https://bundle.social) — The social media management platform these skills support
- [Bundle.social API Docs](https://api.bundle.social) — API documentation
- [mole-skills](https://github.com/antongulin/mole-skills) — macOS system maintenance skills by the same author
