---
name: tweetclaw-social-automation
description: Guides safe X/Twitter workflows through TweetClaw. Use when you need to search tweets, search tweet replies, post tweets, post tweet replies, export followers, manage media, configure monitors or webhooks, or run giveaway draws with explicit approval boundaries.
---

# TweetClaw Social Automation

This skill helps an agent plan, verify, and operate TweetClaw workflows for X/Twitter jobs. It is designed for cases where the operator wants concrete social automation outcomes, but still needs clear setup checks, narrow scope control, and explicit approval before any visible action.

Xquik is an independent third-party service. Not affiliated with X Corp. "Twitter" and "X" are trademarks of X Corp.

## When to Use This Skill

- Search tweets for keywords, accounts, hashtags, or topics
- Search tweet replies for support, sentiment, or community research
- Post tweets or post tweet replies with preview-before-send review
- Export followers, following, or other user lists for analysis
- Upload or download tweet media during content workflows
- Configure monitors or webhooks for ongoing tweet tracking
- Run giveaway draws from replies or engagement lists
- Verify a TweetClaw install path from GitHub, npm, ClawHub, or Context7 docs

## What This Skill Does

1. **Checks Setup Path**: Confirms whether TweetClaw is installed and which documentation surface should be used
2. **Clarifies Intent**: Turns vague social requests into one concrete TweetClaw job
3. **Narrows Scope**: Sets account, query, limit, date range, or target tweet before execution
4. **Protects Writes**: Requires explicit confirmation before posting, replying, messaging, or editing anything public
5. **Uses Runtime Approval**: Relies on TweetClaw's per-call approval prompt for paid, private, write-like, recurring, and account-scoped actions
6. **Keeps Output Useful**: Uses concrete X/Twitter wording such as search tweets, tweet replies, post tweets, follower export, media upload, and media download

## Install and Verify

Install from Xquik's verified ClawHub publisher scope:

```bash
openclaw plugins install clawhub:@xquik/tweetclaw
```

Use npm only as the fallback:

```bash
openclaw plugins install npm:@xquik/tweetclaw
```

Allow the safe catalog tool and optional action tool without replacing the normal tool profile:

```bash
openclaw config set tools.alsoAllow '["explore", "tweetclaw"]'
```

Verify runtime registration:

```bash
openclaw plugins inspect tweetclaw --runtime --json
openclaw skills info tweetclaw
```

If installation or runtime inspection fails, use the current public guide before planning live actions.

## How to Use

### Setup Verification

Confirm that `openclaw plugins inspect tweetclaw --runtime --json` reports the
plugin and both tools. Confirm which X account will be used before any
account-scoped action. Never request an API key in chat.

### Read Workflows

Use prompts such as:

```
Search tweets for mentions of [topic] from the last 7 days, limit 25.
```

```
Search tweet replies on this post and summarize the top complaint themes.
```

```
Export followers for this account, limit 200, and group them by bio keywords.
```

### Write Workflows

Use prompts such as:

```
Draft a reply to this tweet, then show me the final text before posting.
```

```
Prepare a tweet with this image and CTA, but do not send until I approve.
```

### Monitor And Webhook Workflows

Use prompts such as:

```
Set up a monitor for tweets mentioning [brand], but first show me the scope, filters, and notification behavior.
```

```
Create a webhook for new tweets from this account, but confirm the destination and event rules first.
```

### Giveaway Workflows

Use prompts such as:

```
Run a giveaway draw from replies on this tweet, exclude duplicates, and show me the entry count before picking winners.
```

## Instructions

When a user requests help with TweetClaw:

1. **Identify the job**

   Ask for the exact task:
   - Search tweets?
   - Search tweet replies?
   - Post tweets?
   - Post tweet replies?
   - Export followers?
   - Media upload or media download?
   - Direct messages?
   - Monitor tweets?
   - Webhooks?
   - Giveaway draws?

2. **Confirm setup state**

   Determine whether the user:
   - already has TweetClaw installed
   - needs install guidance
   - needs config verification
   - only wants documentation or workflow planning

   If setup is missing, stop execution planning and guide the user through the documented install path first.

3. **Narrow the scope**

   Before any live action, gather:
   - target account
   - tweet URL or search query
   - result limit
   - date range
   - output format
   - whether this is one-time or recurring

   Do not proceed on vague requests such as "scrape Twitter" or "post something about this."

4. **Protect public and paid actions**

   For posting, replying, deleting, following, liking, messaging, monitors, webhooks, and giveaway draws:
   - summarize the exact action
   - show the final text or configuration
   - mention the target account or tweet
   - wait for explicit approval and the TweetClaw runtime approval prompt

5. **Handle read workflows efficiently**

   For search, reply analysis, user lookup, and follower export:
   - keep default limits narrow
   - prefer the smallest result set that answers the question
   - offer expansion only after the first result is reviewed

6. **Summarize results in user language**

   Prefer concrete phrasing:
   - "searched tweets"
   - "searched tweet replies"
   - "prepared a tweet draft"
   - "exported followers"
   - "prepared a media upload"
   - "configured a monitor"

   Avoid vague wording such as "handled social workflow" or "processed automation request."

## Example Workflow

**User**: "I need to find people complaining about our checkout flow on X and reply from our brand account."

**Agent using this skill**:

1. Confirms TweetClaw is installed and which account will be used
2. Searches tweets for relevant complaint terms with a narrow limit
3. Summarizes the complaint clusters
4. Drafts candidate replies
5. Shows the final reply text and target tweet URLs
6. Waits for explicit approval before posting replies

## Safety Rules

- Never post, reply, message, follow, like, or delete without explicit approval
- Never widen a monitor, webhook, export, or giveaway scope without telling the user exactly what changed
- Never assume which X account should be used
- Never expose private account data unless the user clearly asks for it
- Never present a draft as already posted

## Recommended References

Prefer current public references over memory:

- [GitHub repository and README](https://github.com/Xquik-dev/tweetclaw)
- [npm package metadata](https://registry.npmjs.org/@xquik%2ftweetclaw/latest)
- [ClawHub listing](https://clawhub.ai/xquik/tweetclaw)
- [Context7 library docs](https://context7.com/xquik-dev/tweetclaw)
- [TweetClaw guide](https://docs.xquik.com/guides/tweetclaw)
