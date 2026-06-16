---
name: joedevflow
description: Development workflow. Use when building a feature, creating an MVP, refactoring code, fixing a bug, or any task that involves writing or changing implementation code.
argument-hint: "[design|test|implement|debug]"
tools: [AskUserQuestion]
---

Work happens in exactly 4 modes. Operate in one mode at a time.
Do not finish working on a mode without the consent of the user.

---

### How to identify your current mode

If `$ARGUMENTS` is provided, jump directly to that mode:

| `$ARGUMENTS` | Action |
|---|---|
| `design` | Enter Mode 1 — Design |
| `test` | Enter Mode 2 — Test (Red) |
| `implement` | Enter Mode 3 — Implement (Green) |
| `debug` | Enter Mode 4 — Observe & Debug |
| empty | Read HANDOFF.md if present; otherwise ask the user which mode to start in |

Fallback: infer from codebase state

| Mode | You're here when... |
|------|-------------------|
| 1 - Design | No implementation plan exists yet, OR the user asks to plan/architect |
| 2 - Test (Red) | Design is complete; no tests exist yet (or tests need to be written) |
| 3 - Implement (Green) | Failing tests exist; task is to make them pass |
| 4 - Observe & Debug | Tests pass; task is coverage, logging, or a bug was reported |

---

### Mode 1 — Design

**Goal:** Establish the *why*, *what*, and *how* before any code is written.
**Activities:** Ideation, architecture, stack/tooling choices, infrastructure scoping.
**Forbidden:** Writing or editing any code in the codebase.
**Output (contract to Mode 2):** A concrete, agreed spec of what will be built — specific enough that tests can be written against it.

---

### Mode 2 — Test (Red) ⚠️ Most critical mode

**Goal:** Prove the spec is testable before implementation begins.
**Input:** The design contract from Mode 1.
**Activities:**
- Write tests that will pass *only if* the correct behavior is implemented
- Cover happy paths, edge cases, failure modes, and interface boundaries
- Install dependencies / set up boilerplate so tests fail at *assertions*, not imports

**The one rule:** A test that cannot fail for the right reasons is worse than no test.
**Forbidden:** Writing implementation code (test scaffolding/boilerplate is the only exception).
**Output (contract to Mode 3):** Full test suite — all red, all failing at assertions.

---

### Mode 3 — Implement (Green)

**Goal:** Make the red tests pass.
**Input:** The failing test suite from Mode 2.
**Activities:** Write implementation code guided by what the tests express.
**Forbidden:** Editing tests. If a test seems wrong, stop and ask the user — do not modify it.
**Output (contract to Mode 4):** All tests passing. No test was changed.

---

### Mode 4 — Observe & Debug

**Goal:** Verify the system works end-to-end and regressions are caught.
**Activities:**
- Run coverage; flag untested lines to the user
- Write e2e tests that exercise the system from the outside — real inputs, real outputs, no mocks
- If a bug is found: understand it, fix it, add a **regression test** before touching the code

**Forbidden:** Fixing a bug before writing a regression test that reproduces it.
**Output:** Coverage report, e2e tests passing, zero known regressions.

---

**Context note:** Each mode may run in a separate agent/context window.
Treat the mode's input contract as the only shared state you can rely on.

### Mode Handoff

At the end of each mode,check whether to proceed:

**If the `AskUserQuestion` tool is available**, call it with these options:
- "Yes — write HANDOFF.md" → write the handoff (see format below)
- "No — skip it" → do not write the file; just summarize the mode in chat
- "Hold on — we're not done with this mode yet" → remain in the current mode; do not write

**If `AskUserQuestion` is not available**, default to writing the handoff.

Overwrite `HANDOFF.md` at the repository root, in case it exists. `HANDOFF.md` is the canonical cross-mode handoff artifact. It should contain the latest authoritative handoff, replacing any previous handoff content unless the user explicitly asks for a historical log.

**Mode:** <DESIGN | TEST_RED | IMPLEMENT_GREEN | OBSERVE_DEBUG>
**Goal:** <what this mode was trying to accomplish>
**Inputs used:** <user request, files read, tests examined, errors seen>
**Changes made:** <specific files edited or created — paths and a one-line summary each>
**Outputs produced:** <design doc, list of failing tests with names, passing test run output, debug findings>
**Open issues:** <blockers, risks, unknowns — be specific, not vague>
**Next recommended mode:** <next mode + one sentence on why>
