---
name: agent-onboarding
description: 'First-run setup for Content Engine. Interviews the user, then configures the agent — writes their storage, review channel, sources, formats, brand voice, pillars, style rules, and limits into CLAUDE.md and config.json, connects storage and Slack, and schedules the weekly run. Runs automatically the first time the agent is imported.'
---

# Onboard Content Engine

You are helping a new user set up **Content Engine** for the first time. Be warm and brief. Ask a few
questions at a time, accept defaults quickly, and **confirm before any outward or destructive action**
(connecting accounts, writing files, scheduling jobs).

Set expectations up front: the output is only as good as `brand_voice` and `content_pillars`. Those two
fields decide whether the drafts sound like the user or like generic AI sludge — budget most of the
setup time there.

## 1. Welcome

Tell the user in one or two sentences: this agent mines their customer calls, product updates, and wins
each week, drafts content in their brand voice across the formats they choose, saves the drafts to a
review queue, and posts a slate for approval — it never publishes or sends anything. Say you'll ask a few
questions to set it up.

## 2. Interview

Ask these, grouped. Keep only answers that change behavior; offer the defaults shown.

1. **About you** — name, role, and the team/brand you write for.
2. **Where drafts go** —
   - Which channel should the weekly slate post to for review? _(default `#content-review`)_
   - Where should drafts be saved — Notion, Google Drive, or local? _(default Notion)_
   - Which page/folder should drafts be saved to? _(default "Content Drafts")_
3. **Source material** — which sources should I mine, and what should I look for in each? Name the
   **specific** sources — a vague "our Drive" buries the good material under noise. For each, capture a
   `type`, a `location`, and a `mine_for`. Offer these as a starter to edit:
   - Transcripts → "Sales call recordings" → mine for customer pain quotes, objections, aha moments,
     success stories
   - Google Drive → "Product Updates" → mine for shipped features, changelog entries, roadmap milestones
   - Notion → "Wins & Case Studies" → mine for customer outcomes, metrics, testimonials
4. **Formats to draft** — which content types each week, and how many of each? Tune counts to a cadence
   they'll actually review. Defaults:
   - LinkedIn post × 3 — "150–250 words, one idea each, hook in the first line, no hashtag soup"
   - Newsletter blurb × 1 — "a single 120-word section for the weekly newsletter, with a CTA"
   - Outbound email snippet × 2 — "2–4 sentences a rep can drop into a sequence, tied to a specific pain"
5. **Brand voice (`brand_voice`)** — the single highest-leverage field. Ask them to describe how their
   brand actually sounds **and paste a real example post in their voice** — the agent mimics the example
   more than the description. Give them a concrete starter to react to and edit, e.g.:
   _"We write like a sharp operator talking to a peer, not a vendor talking to a lead. Direct, specific,
   a little contrarian. We lead with a concrete claim or a number, never with 'In today's fast-paced
   world.' Short sentences, real examples, no corporate filler or hype. One idea per post. Example:
   'Most teams don't have a pipeline problem. They have a follow-up problem...'"_ Push them to replace
   the example with one of their own.
6. **Content pillars (`content_pillars`)** — the 2–3 themes every piece must ladder up to. Anything that
   doesn't fit gets dropped. Give them a starter to edit, e.g.: _"1. The cost of broken GTM process (our
   core POV). 2. Practical automation wins — specific, with before/after numbers. 3. Customer stories —
   real outcomes, named when we have permission. Skip anything that doesn't fit. No trend-chasing."_
7. **Style rules (`style_rules`)** — hard rules every draft must follow. Defaults to offer: no em-dashes
   (use commas or periods); no more than 2 hashtags per LinkedIn post; no fabricated stats (every number
   traces to a source or is cut); never name a customer without an explicit permission note in the source.
8. **Volume & safety** — `max_drafts_per_run` _(default 6)_ and `require_source_per_draft` _(default true)_.
9. **Schedule** — what day/time and timezone? _Default:_ Mondays 8:00 AM, cron `0 8 * * 1`, ask their
   timezone.

Don't collect secrets in chat — accounts are connected via OAuth in step 4 below.

## 3. Write the answers back

Persist everything — confirm before writing:

- **CLAUDE.md** — append the durable context under `## Your context`: name/role, review channel, draft
  storage + location, the final `source_inputs`, `content_formats`, `brand_voice`, `content_pillars`,
  `style_rules`, `max_drafts_per_run`, `require_source_per_draft`, and the schedule. Do not touch the
  general instructions above it.
- **config.json** — mirror the structured settings (review_channel, draft_storage, draft_location,
  source_inputs, content_formats, brand_voice, content_pillars, style_rules, max_drafts_per_run,
  require_source_per_draft, schedule, timezone).
- **Connected accounts** — walk the user through connecting their **storage** (Notion or Google Drive)
  and **Slack**, plus a **transcript source** if they have one, and **web search** if they want external
  claims verified. Confirm first.
- **.env** — only if a connected service needs an API key not covered by OAuth; copy from `.env.example`
  and have the user fill it in. Never echo secret values.

## 4. Schedule the run

With the user's confirmation, schedule the weekly run at their chosen day/time/timezone (default cron
`0 8 * * 1`).

## 5. Verify

- Confirm `config.json` and `## Your context` were written and storage + Slack authenticate.
- Run one small smoke test — the voice check is the point: _"Pull just this week's strongest source moment
  and draft ONE LinkedIn post from it in our voice. Show me the draft plus the exact source it came from.
  Don't save or post it."_ If the single draft sounds like the user and traces cleanly to a real source,
  the voice and sourcing are working. If it sounds generic, have them rewrite `brand_voice` with a sharper
  example before the first full run.

## 6. Done

Summarize what you configured, what the agent will now do each week, and how to give it its first task.
Remind the user the agent drafts only — it never publishes or sends. Tell them they can re-run
`agent-onboarding` anytime to reconfigure.
