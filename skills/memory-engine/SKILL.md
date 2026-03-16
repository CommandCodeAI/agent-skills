---
name: memory-engine
description: >
  Store and retrieve long-term knowledge across sessions with semantic naming and hybrid search.
  Use when you need to remember something for the future, recall past decisions, look up prior context,
  or search what was discussed or built in a previous session.
user-invocable: true
---

# Memory Engine 🧠

Persistent, searchable memory across all sessions. Storage uses semantic file naming and hybrid search (semantic + keyword fallback).

## When to Use This Skill

- "Remember that…" / "Don't forget…" → store a memory
- "What did we decide about…" / "What have we talked about…" → search memory
- "What's the status of…" → search memory
- Start of any new session — search relevant topics before answering
- After completing important work — store a summary immediately

## How It Works

**Storage:** Memory files use semantic naming convention:
```
YYYY-MM-DD__[CATEGORY]__[TOPIC]__[CONTEXT].md
```

**Search:** Hybrid approach:
1. Try semantic search first (embeddings-based)
2. Expand query with synonyms if sparse results
3. Fall back to keyword search if semantic unavailable
4. Return diagnostics showing which methods were used

## Commands

### Store a Memory
```bash
memory_store "[fact or summary]" \
  --category [briefing|strategy|audit|vision|code|project|bug|feature|research|decision|general] \
  --topic [your-topic] \
  --context [optional-descriptor]
```

### Search Memory (Enhanced)
```bash
memory_search "[query]" --limit 10 --diagnostics
```

### Search Memory (Basic Fallback)
```bash
memory_search_basic "[query]" --limit 10
```

### Check Memory Health
```bash
memory_health
```

## File Naming Convention

Memory files follow a semantic naming pattern:

```
YYYY-MM-DD__[CATEGORY]__[TOPIC]__[CONTEXT].md
```

**Categories:** briefing, strategy, audit, vision, code, project, bug, feature, research, decision, general

**Examples:**
- `2026-02-25__briefing__morning-signal__daily.md`
- `2026-02-24__strategy__architecture__design.md`
- `2026-02-24__audit__database__schema.md`
- `2026-02-20__decision__authentication__oauth.md`

## Examples

```bash
# Store a decision
memory_store \
  "Decided to use semantic file naming with YYYY-MM-DD__CATEGORY__TOPIC__CONTEXT pattern" \
  --category decision --topic memory-engine --context naming

# Store a briefing summary
memory_store \
  "Morning briefing sent successfully to 142 subscribers with 8 key insights" \
  --category briefing --topic daily-briefing --context summary

# Search for past decisions
memory_search "authentication oauth" --limit 5

# Exploratory search with diagnostics
memory_search "what have we decided about architecture" --limit 5 --diagnostics
```

## Search Behavior

The enhanced search engine automatically:

1. **Detects query type** (factual / conceptual / exploratory) and adjusts relevance threshold
2. **Tries semantic search** first using embeddings
3. **Expands query** with synonyms if results are sparse
4. **Falls back to keyword search** if semantic search is unavailable or returns nothing
5. **Returns diagnostics** showing which methods were used and why

## Guardrails

- **Always store** important facts, decisions, and task completions immediately after they happen
- **Always search** before answering questions about past sessions — never assume context is absent
- Use `--diagnostics` when a search returns no results to understand why
- If enhanced search is unavailable, fall back to basic keyword search
- Store the **summary of significant changes**, not just raw data — make it human-readable for future retrieval
- Keep memory entries concise but complete (50-500 words)
- Use consistent category and topic names across sessions for better search results

## Integration

This skill works best when:
- Invoked at the start of each session to recall relevant context
- Used after completing major work to store summaries
- Combined with other skills that need historical context
- Integrated into agent workflows for persistent learning

## Technical Notes

- Semantic search requires embeddings API (e.g., Google Generative AI)
- Keyword search works offline without external dependencies
- Memory files are stored as markdown for human readability
- Search results are scored by relevance and recency
