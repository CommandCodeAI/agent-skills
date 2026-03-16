---
name: football-live-scores
description: Check live and recent scores plus league tables for the English Premier League and UEFA Champions League. Use when the user asks about EPL/Premier League or Champions League scores, fixtures, or standings.
---

# Football Live Scores & Tables

This skill helps you fetch and summarize **live or very recent football scores and league tables** for:

- The **English Premier League (EPL)**
- The **UEFA Champions League (UCL)**

It assumes you have access to web/search or HTTP tools. If you do **not** have live internet access in the current environment, you must clearly explain that you cannot provide real‑time data.

## When to Use This Skill

Use this skill when the user asks for:

- Current or very recent **EPL scores** (e.g. “what’s the Arsenal score right now?”)
- The **Premier League table/standings** (overall or for a specific team)
- **Champions League live scores** or most recent match results
- **Champions League group tables** or knockout fixtures
- Comparisons like “who is top of the Premier League?” or “who is leading Group A?”
- Upcoming fixtures *specifically* for the EPL or Champions League

Do **not** use this skill for:

- Other leagues (La Liga, Serie A, etc.) unless the user clearly mixes them and EPL/UCL
- Historical stats and deep analytics beyond recent matches and tables
- Non‑football sports

If the user’s request mixes EPL/UCL with other unrelated topics, address only the football part with this skill and explicitly handle or defer the rest.

## Data Sources & Reliability

When you have web or HTTP tools, prefer **authoritative, up‑to‑date sources**, for example:

- Official competition sites (e.g. Premier League, UEFA)
- Major sports outlets (e.g. BBC, Sky Sports, ESPN, Livescore, FlashScore, Sofascore)

Guidelines:

- Prefer sources that show **timestamps**, **match status** (FT, HT, Live, Postponed), and **table last‑updated times**.
- If multiple sources disagree, prefer **official competition sites**, then reputable news/sports sites.
- Always include the **date**, **competition**, and **time zone** when summarizing.

If **no web or HTTP access** is available:

- Say clearly that you cannot access live scores in this environment.
- Offer alternatives (e.g. “Here’s how you can check on the official Premier League site…”).

## Instructions: EPL Live Scores

When the user asks about **EPL live scores or latest results**:

1. **Clarify the request** if needed:
   - Are they asking about a specific **team**, **match**, **matchday**, or **all current live games**?
   - Are they interested in **today’s fixtures**, **latest finished results**, or **currently in‑progress matches**?
2. **Search** using your web/HTTP tools:
   - Query including competition, date, and team if provided (e.g. “Premier League live scores Arsenal today”).
3. **Identify the relevant matches**:
   - Filter by competition = **Premier League** (EPL).
   - Confirm the **match date** and **kickoff time** relative to the user’s presumed time zone.
4. **Extract for each relevant match**:
   - Home team and away team
   - Current score
   - Match status: Not started, Live (with minute/added time), HT, FT, Postponed
   - If available: goalscorers and important events (penalties, red cards)
5. **Summarize concisely**:
   - Group by competition and match status (e.g. Live, Finished, Upcoming).
   - Always state the **date**, **competition**, and **source**.
6. **Mention staleness**:
   - If the page clearly indicates a last update time, mention it.
   - If not available, note that times may be slightly delayed.

### EPL Live Scores – Example Output

> As of 20:45 BST on 12 May 2026, in the Premier League:
>
> - **Arsenal 2–1 Liverpool (73')** – Live. Goals: Saka (12'), Ødegaard (39'); Salah (58').  
> - **Chelsea 0–0 Newcastle (HT)** – Half‑time at Stamford Bridge.  
>
> Source: Official Premier League live scores.

## Instructions: EPL League Table

When the user asks for the **Premier League table/standings**:

1. **Confirm scope**:
   - Full table vs. only a specific team.
   - Overall table vs. home/away tables (if the site shows variants).
2. **Fetch the official or trusted standings page**.
3. **Extract key fields**:
   - Position, Club, Played (P), Wins (W), Draws (D), Losses (L), Goals For (GF), Goals Against (GA), Goal Difference (GD), Points (Pts).
4. **Summarize**:
   - For the full table, show **top N** teams (e.g. top 6 or top 10), and optionally the bottom 3 for relegation context.
   - For a specific team, show **their row** in the table plus immediate neighbours (one above and one below).
5. **Include metadata**:
   - Date, “as of last update”, and source.

### EPL Table – Example Output

> **Premier League table (top 6)** – as of 12 May 2026  
> 1. Man City – P32, W22, D6, L4, GF72, GA25, GD+47, **Pts 72**  
> 2. Arsenal – P32, W21, D7, L4, GF68, GA28, GD+40, **Pts 70**  
> 3. Liverpool – P32, W20, D8, L4, GF65, GA29, GD+36, **Pts 68**  
> 4. Aston Villa – …  
> 5. Tottenham – …  
> 6. Newcastle – …  
>
> Source: Official Premier League table (may be delayed by a few minutes).

## Instructions: Champions League Live Scores

When the user asks about **Champions League live scores or recent results**:

1. **Clarify competition**:
   - Confirm they mean **UEFA Champions League** (not Europa League or Conference League).
2. **Search** for live or recent scores:
   - Include stage if specified (group stage, quarter‑finals, etc.) and date.
3. **Filter by competition** = UEFA Champions League.
4. **Extract per match**:
   - Home team, away team, score, match status, and stage (e.g. Group A, Round of 16 second leg).
5. **Summarize**:
   - Group by stage or kickoff time.
   - Highlight aggregate scores in knockout ties (e.g. “3–2 on aggregate”).
6. **Mention timing and source** just like for EPL.

### UCL Live Scores – Example Output

> **UEFA Champions League – Quarter‑finals (second legs)** – as of 21:15 CET  
>
> - **Real Madrid 1–1 Man City (60')** – 2–2 on aggregate, away‑goals removed, heading to extra time if still level.  
> - **Bayern 2–0 PSG (FT)** – Bayern advance 4–1 on aggregate.  
>
> Source: Official UEFA live scores.

## Instructions: Champions League Tables (Groups)

For **group stage tables**:

1. Identify which **group(s)** the user cares about (e.g. Group A, “Barcelona’s group”).
2. Fetch a reputable standings page showing **group tables**.
3. For each requested group, extract:
   - Position, Club, Played, Wins, Draws, Losses, GF, GA, GD, Points.
4. Summarize group standings and note:
   - Which teams are currently in qualifying positions.
   - Remaining matches if clearly listed.

## Handling Time Zones & Dates

Always:

- Mention the **time zone** of times you report (e.g. BST, CET, UTC).
- If the user is in a different region (e.g. they mention their city), clarify or convert times when helpful.
- Distinguish clearly between:
  - **Past results** (FT)
  - **Live matches**
  - **Upcoming fixtures**

If the user asks for “today’s games” but it’s already past midnight in the source’s time zone, clarify the date you are using.

## Error Handling & Limitations

If you cannot access live data:

- Say explicitly:  
  > “I don’t have live internet access in this environment, so I can’t fetch real‑time scores or tables right now.”
- Offer a brief set of manual steps the user can follow on official sites.

If no matches are in progress:

- Return the **most recent finished matches** for that competition and say that no games are currently live.

If tables or scores look inconsistent across sources:

- Prefer official competition sources.
- If still inconsistent, explain the discrepancy instead of guessing.

## Example Prompts

- “What’s the current Premier League table?”  
- “Who is top of the Premier League right now and by how many points?”  
- “What’s the Arsenal score in the Premier League game tonight?”  
- “Show me today’s Champions League scores.”  
- “Give me the current Champions League Group A table.”  
- “Summarize this week’s Champions League results with scores and which teams advanced.”

