---
name: site-automation
description: >
  Manage website content via automation APIs. Sync GitHub projects, generate changelogs,
  create posts, send newsletters, manage comments, and check health. Use when any task
  involves website content management or newsletter operations.
user-invocable: true
---

# Site Automation 🌐

Manage website content through automation APIs. Sync GitHub projects, generate changelogs, create posts, send newsletters, and manage comments.

## When to Use This Skill

- "Sync the latest GitHub projects"
- "Generate a changelog from recent commits"
- "Create a blog post"
- "Send a newsletter"
- "Check recent comments on posts"
- "Reply to a comment"
- "List newsletter subscribers"

## Prerequisites

Set up environment variables:
```bash
export SITE_BASE_URL="http://localhost:3000"  # or your site URL
export CLAW_AUTOMATION_KEY="your-api-key"     # Bearer token for API auth
export GITHUB_USERNAME="your-github-user"     # GitHub user for project sync
```

Store these in your `.env` file for persistence.

## Commands

### Health Check
```bash
site_automation health
```

### Full Sync (Projects + Changelog)
```bash
site_automation full-sync
```

Syncs GitHub projects to database and generates changelog from recent commits.

### Sync Projects Only
```bash
site_automation sync-projects
```

Pulls latest GitHub repositories and updates project database.

### Sync Changelog Only
```bash
site_automation sync-changelog
```

Generates changelog entries from recent git commits.

### Create a Blog Post
```bash
site_automation create-post \
  --slug post-slug \
  --title "Post Title" \
  --content-file /path/to/content.md \
  --type blog \
  --tags tag1 tag2 tag3
```

### Create a Changelog Post
```bash
site_automation create-post \
  --slug changelog-slug \
  --title "Changelog Title" \
  --content-file /path/to/content.md \
  --type changelog
```

### Send Newsletter
```bash
site_automation send-newsletter \
  --subject "Newsletter Subject" \
  --html-file /path/to/email.html \
  --idempotency-key unique-key-for-deduplication
```

### List Subscribers
```bash
site_automation list-subscribers
```

### List Recent Comments
```bash
site_automation list-comments --since 2026-02-20
```

### Reply to a Comment
```bash
site_automation reply-comment \
  --post-id POST_UUID \
  --body "Your reply text" \
  --source-comment-id COMMENT_UUID
```

## API Endpoints (Direct)

If you need to call the API directly:

| Method | Endpoint | Purpose |
|--------|----------|---------|
| GET | `/api/automation/health` | Health check |
| POST | `/api/automation/projects/sync` | GitHub → projects DB |
| POST | `/api/automation/changelog/github` | Commits → changelog posts |
| POST | `/api/automation/posts` | Create blog/changelog post |
| GET | `/api/automation/comments` | Poll recent comments |
| POST | `/api/automation/comments/respond` | Reply to comment |
| GET | `/api/automation/newsletter/subscribers` | List subscribers |
| POST | `/api/automation/newsletter/send` | Send newsletter |

**Auth header:** `Authorization: Bearer <CLAW_AUTOMATION_KEY>`

## Workflow: Publish Article from Intelligence

1. Generate article content (from briefing, research, or manual writing)
2. Write content to a temporary `.md` file
3. Call `create-post` with the file
4. Optionally send newsletter linking to the new post

## Examples

```bash
# Full sync before publishing
site_automation full-sync

# Create a blog post
site_automation create-post \
  --slug "ai-trends-2026" \
  --title "AI Trends in 2026" \
  --content-file ./article.md \
  --type blog \
  --tags ai trends 2026

# Send newsletter
site_automation send-newsletter \
  --subject "Weekly Digest — Feb 25, 2026" \
  --html-file ./newsletter.html \
  --idempotency-key "digest-2026-02-25"

# Check recent comments
site_automation list-comments --since 2026-02-20

# Reply to a comment
site_automation reply-comment \
  --post-id "550e8400-e29b-41d4-a716-446655440000" \
  --body "Thanks for the feedback!" \
  --source-comment-id "6ba7b810-9dad-11d1-80b4-00c04fd430c8"
```

## Integration Patterns

### With Briefing Pipeline
The daily briefing automatically runs `full-sync` before synthesizing the newsletter. This ensures:
- New GitHub projects are synced to the database
- Recent commits become changelog entries
- Subscriber list is current before send

### With Content Pipeline
Use in content creation workflows:
1. Research/write content
2. Store in temporary file
3. Call `create-post` to publish
4. Trigger newsletter send if needed

### With Comment Moderation
Monitor comments and respond:
1. Poll recent comments with `list-comments`
2. Review for moderation
3. Reply with `reply-comment` or flag for manual review

## Response Format

After execution, report:
- Counts (synced, created, sent)
- Any errors or warnings
- Next steps if applicable

## Guardrails

- Always run `health` check before major operations
- Use idempotency keys for newsletter sends to prevent duplicates
- Validate markdown content before posting
- Store API key securely (never hardcode)
- Test with `--draft` flag before publishing
- Monitor rate limits on GitHub API calls
- Keep changelog entries concise and user-focused
