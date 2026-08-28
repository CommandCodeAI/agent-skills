---
name: hol-guard
description: Sets up and operates HOL Guard for supported local AI coding harnesses, validates protection health, reviews blocked actions, and retrieves receipts. Use when a user asks to install HOL Guard, add a local runtime policy boundary to Codex, Claude Code, Cursor, Gemini CLI, Copilot CLI, Hermes, OpenClaw, OpenCode, or Antigravity, or inspect a Guard block.
---

# HOL Guard

HOL Guard provides a local policy and approval boundary before tools run in supported AI coding harnesses. Use this skill to install Guard, attach it to a supported harness, validate the boundary, and inspect approvals or receipts.

## When to Use This Skill

Use this skill when the user wants to:

- install or configure HOL Guard;
- protect a supported local AI coding harness before tool execution;
- validate that Guard is healthy for a detected harness;
- inspect a blocked or approval-gated action;
- review Guard receipts, inventory, events, or diffs.

## Safety Rules

- Treat HOL Guard as a local agent-runtime boundary. Do not claim it protects a remote provider API or replaces that provider's authentication, RBAC, quotas, or audit controls.
- Do not claim Command Code itself is protected by HOL Guard unless `hol-guard detect --json` explicitly reports a supported Command Code adapter. The currently documented harness list does not include Command Code.
- Never read `.env` files while setting up Guard.
- Never bypass a Guard approval or silently disable Guard because setup failed.
- Never approve a queued action without showing the user the risk reason and requested scope first.
- Prefer Guard-owned harness configuration over manual edits to agent configuration files.
- Do not report a harness as protected until Guard commands prove it.

## Prerequisite Check

Check for the CLI directly:

```bash
hol-guard --version
```

If it is missing and the user asked to install Guard, prefer an isolated CLI install:

```bash
pipx install hol-guard
```

If `pipx` is unavailable, explain that an isolated install is recommended rather than silently modifying the user's system Python environment.

## Detect the Harness

Run detection before choosing an adapter:

```bash
hol-guard detect --json
```

Use the exact detected harness name. Supported documented targets include:

- `codex`
- `claude-code`
- `copilot`
- `cursor`
- `gemini`
- `hermes`
- `openclaw`
- `opencode`
- `antigravity`

If the user's active harness is not reported as supported, stop before claiming protection and explain that Guard does not currently have a verified adapter for that harness.

## Set Up Protection

For a detected supported harness:

```bash
hol-guard bootstrap
hol-guard install <harness>
hol-guard run <harness> --dry-run
hol-guard doctor <harness> --json
hol-guard run <harness>
hol-guard status
```

The dry run and doctor are validation gates. If either fails, troubleshoot the reported failure instead of proceeding as though the boundary is active.

For Hermes, use its harness-specific bootstrap when appropriate:

```bash
hol-guard hermes bootstrap
```

## Inspect Blocked Work

When Guard blocks or queues an action, inspect the request before changing its state:

```bash
hol-guard approvals
hol-guard receipts
hol-guard diff <harness>
```

For terminal-only resolution, and only after the user understands the request:

```bash
hol-guard approvals approve <request-id>
hol-guard approvals deny <request-id>
```

Do not infer approval from the user's general intent. Approval should be tied to the specific request ID and reviewed scope.

## Collect Evidence

Use Guard's evidence commands when the user needs an audit trail or proof of current state:

```bash
hol-guard receipts
hol-guard inventory
hol-guard abom --format json
hol-guard events
hol-guard explain <artifact-id>
```

For cloud synchronization, keep it explicit and user-directed:

```bash
hol-guard connect status
hol-guard sync
```

## Troubleshooting

Start with the narrowest diagnostic command:

```bash
hol-guard doctor <harness> --json
hol-guard detect --json
hol-guard settings show
```

If the harness is not detected, do not guess an adapter name. If Guard reports a configuration conflict, preserve the user's existing configuration and surface the conflict before making additional changes.

## Examples

### Protect a detected Claude Code workspace

```bash
hol-guard detect --json
hol-guard bootstrap
hol-guard install claude-code
hol-guard run claude-code --dry-run
hol-guard doctor claude-code --json
hol-guard run claude-code
hol-guard status
```

### Review a blocked action

```bash
hol-guard approvals
hol-guard receipts
```

Read the request and risk reason, then ask the user whether that specific request should be approved or denied.

## Response Checklist

When reporting Guard work, include:

- which Guard command ran;
- which harness Guard detected;
- whether the validation gates passed;
- what remains blocked or risky;
- what receipt, event, or diagnostic output supports the conclusion.

Never claim protection, approval, or readiness without command output that proves it.
