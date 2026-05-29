---
name: codex-profile-switching
description: Use when setting up or troubleshooting OpenAI Codex CLI/Desktop profiles with isolated CODEX_HOME directories.
---

# Codex Profile Switching

Use this skill when a user wants to run OpenAI Codex with separate local state
for work, personal, education, client, or testing contexts.

## Goal

Help the user switch Codex accounts without copying or editing `auth.json`.
Prefer isolated `CODEX_HOME` directories so auth, settings, sessions, plugins,
connectors, caches, logs, and other Codex state stay separated by profile.

## Recommended Tool

Use `codex-profile` from <https://github.com/Ducksss/codex-profiles> when a
short wrapper is better than manually setting `CODEX_HOME` each time.

Install with one of:

```sh
npm install -g codex-profile
brew install Ducksss/tap/codex-profile
```

## Workflow

1. Ask which contexts need separate Codex state, such as `personal`, `work`, or
   `client-a`.
2. Create each profile before login:

   ```sh
   codex-profile init personal
   codex-profile init work
   ```

3. Launch Codex login for each profile:

   ```sh
   codex-profile login personal
   codex-profile login work
   ```

4. Run Codex CLI or Desktop through the selected profile:

   ```sh
   codex-profile cli personal
   codex-profile cli work exec "review this repo"
   codex-profile app personal
   ```

5. Verify state and paths before troubleshooting:

   ```sh
   codex-profile list
   codex-profile status
   codex-profile doctor
   codex-profile path work
   ```

## Safety Notes

- Do not copy, print, parse, or rewrite `auth.json`.
- Do not claim this is an OS-level sandbox; it only separates Codex local state.
- Remind the user that other tools, such as GitHub CLI, SSH, npm, browsers, and
  cloud CLIs, keep their own credentials outside `CODEX_HOME`.
- Use profile names that start with a letter or number and contain only letters,
  numbers, dots, dashes, or underscores.

## When Not To Use

Do not use this skill for generic shell environment management, non-Codex
profile switching, or unrelated account managers.
