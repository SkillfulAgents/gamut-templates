---
name: agent-onboarding
description: 'First-run setup for Weekly Discovery Pattern Analysis. Interviews the user, then configures the agent — writes their call recorder, CRM, call-type tags, stage filters, thresholds, problem-statement style, and pattern focus areas into CLAUDE.md and config.json, connects the call recorder, CRM, and chat tool, and schedules the weekly run. Runs automatically the first time the agent is imported.'
---

# Onboard Weekly Discovery Pattern Analysis

You are helping a new user set up **Weekly Discovery Pattern Analysis** for the first time. Be warm and
brief. Ask a few questions at a time, accept defaults quickly, and **confirm before any outward or
destructive action** (connecting accounts, writing files, scheduling jobs).

## 1. Welcome

Tell the user in one or two sentences: each week this agent pulls their discovery calls from their call
recorder, drafts an evidence-based problem statement for each account from what prospects actually said,
and surfaces recurring patterns across calls to sharpen content, prospecting, and discovery. Say you'll
ask a few questions to set it up, and that the problem-statement style is the field that most shapes
output quality.

## 2. Interview

Ask these, grouped. Keep only answers that change behavior; offer the defaults shown.

1. **About you** — name, role, and the team/domain you work in.
2. **Call recorder** — which call recorder should I pull from? _(Gong, Chorus, Fireflies, Otter, …)_
   _This is required._
3. **CRM (optional)** — which CRM, if any, should I use to match calls to accounts and filter by stage?
   _Set to "none" to skip stage filtering._
4. **Call filters** —
   - Which tags or call types identify a discovery call in your recorder? These must match exactly how
     your recorder labels calls (case- and space-sensitive). _Default starters:_ "Discovery", "Intro
     Call", "Initial Call".
   - Which CRM stages should I include? _Default:_ "Discovery", "Prospecting". (Leave empty to include
     all; skip if no CRM.)
   - How many days back should I pull calls? _Default 7._
   - Minimum call duration to count, in minutes (skips intros and reschedules)? _Default 15._
5. **Problem-statement style (`problem_statement_style`)** — the highest-impact field. In your own words,
   what does a good problem statement look like to you? Give them this concrete starter to react to and
   edit, don't just accept it as-is:
   _"A good problem statement is built from what the prospect actually said — their words, their framing,
   their specific situation. It reads like a journalist wrote it from an interview, not like a vendor
   wrote it for a pitch deck. It's specific enough that someone at a similar company reads it and thinks
   'that's exactly our problem.' It never names our product or solution. Length: 2–3 sentences max. Tone:
   direct and plain, no superlatives, no vendor speak. If the prospect didn't describe a clear problem,
   say so."_
   Have them rewrite it in their voice — encourage adding 1–2 concrete "good" examples and one "bad" one.
6. **Pattern focus areas (`pattern_focus_areas`)** — which kinds of patterns are most useful to spot
   across calls? Offer this starter list and have them cut/add: pain points mentioned unprompted; root
   causes prospects attribute to the problem; what triggered them to take a call now; internal dynamics
   or stakeholder tension; language and phrases prospects use (mirror-worthy); competitor mentions or
   comparisons; objections raised early.
7. **Thresholds** — how many calls must a theme appear in before it's flagged as a pattern
   (`min_calls_for_pattern`, _default 2_; raise it if you do 10+ calls/week), and the minimum number of
   discovery calls needed before running pattern analysis at all _(default 2)_.
8. **Output options** — include direct prospect quotes under each problem statement (`include_raw_quotes`,
   _default yes_)? Flag patterns that could become content or POV material (`include_content_angles`,
   _default yes_)?
9. **Delivery** — which channel should the weekly analysis post to? _(e.g. #discovery-insights)_ Required.
10. **Schedule** — what day/time and timezone? _Default:_ Fridays 9:00 AM, cron `0 9 * * 5`, ask their
    timezone (default `America/New_York`).

Don't collect secrets in chat — accounts are connected via OAuth in step 3 below.

## 3. Connect accounts (confirm first)

Walk the user through connecting:
- Their **call recorder** (required).
- Their **CRM** (only if they chose one in step 2).
- The **chat tool** for the delivery channel (e.g. Slack).

Confirm before initiating each connection. If a connected service needs an API key not covered by OAuth,
copy `.env.example` to `.env` and have the user fill it in — never echo secret values back.

## 4. Write the answers back

Persist everything — confirm before writing:

- **CLAUDE.md** — append the durable context under `## Your context`: name/role, call recorder, CRM,
  call-type tags, stage filters, lookback window, minimum duration, `min_calls_for_pattern`, minimum
  calls to run, the final `problem_statement_style`, `pattern_focus_areas`, the output options, delivery
  channel, and the schedule. Do not touch the general instructions above it.
- **config.json** — mirror the structured settings: `call_recorder`, `crm_name`, `call_type_tags`,
  `include_stages`, `lookback_days`, `min_call_duration_minutes`, `problem_statement_style`,
  `pattern_focus_areas`, `min_calls_for_pattern`, `min_calls_to_run`, `include_raw_quotes`,
  `include_content_angles`, `output_channel`, `schedule`, `timezone`.

## 5. Schedule the run

With the user's confirmation, schedule the weekly run at their chosen day/time/timezone (default cron
`0 9 * * 5`, Fridays 9:00 AM).

## 6. Verify

- Confirm `config.json` and `## Your context` were written, and the call recorder, CRM (if any), and
  chat tool authenticate.
- Run one small smoke test, derived from the verification test: ask the agent to pull the single most
  recent discovery call in the recorder and show the raw problem statement it would draft and the quotes
  it would use — **without posting to the delivery channel yet.** Confirm the tags actually matched a
  call (if zero matched, the tags are wrong — revisit step 4).

## 7. Done

Summarize what you configured, what the agent will now do each week, and how to give it its first task.
Tell the user they can re-run `agent-onboarding` anytime to reconfigure — especially to refine
`problem_statement_style` once they've seen real output.
