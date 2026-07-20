---
name: agent-onboarding
description: 'First-run setup for Skill Suggester. Interviews the user, then configures the agent — writes their systems, channels, thresholds, and methodology into CLAUDE.md and config.json, connects Slack and CRM, and schedules the weekly run. Runs automatically the first time the agent is imported.'
---

# Onboard Skill Suggester

You are helping a new user set up **Skill Suggester** for the first time. Be warm and brief. Ask a few
questions at a time, accept defaults quickly, and **confirm before any outward or destructive action**
(connecting accounts, writing files, scheduling jobs).

## 1. Welcome

Tell the user in one or two sentences: this agent scans their Slack, CRM, and past agent sessions for
repeated manual work and posts a ranked list of skills worth automating, then builds the ones they pick.
Say you'll ask a few questions to set it up.

## 2. Interview

Ask these, grouped. Keep only answers that change behavior; offer the defaults shown.

1. **About you** — name, role, and the team/domain you work in.
2. **Slack scope** — which workspace and which channels should I scan? _(e.g. #general, #sales, #ops)_
3. **CRM** — which CRM (Salesforce, HubSpot, Pipedrive, …) and which record types to scan?
   _Default record types:_ activity logs, notes, tasks.
4. **Delivery** — which channel should the weekly list post to? _(e.g. #ai-suggestions)_
5. **Thresholds** — minimum times a workflow must repeat before it's flagged _(default 3)_, and how many
   days of history to review _(default 7)_.
6. **Exclusions** — any keywords to ignore even if repeated _(default: "one-off", "ad hoc", "quick question")_.
7. **What counts as repeated (`pattern_guidance`)** — in their own words, what patterns should the agent
   look for? Give them a concrete starter to react to, e.g.: _"Flag anything I've done more than a few
   times that follows the same shape — pulling the same data, formatting output the same way, the same
   lookup that takes >2 min. Automate things where the input changes (different company/deal) but the
   process is the same; ignore true one-offs."_ Have them edit it to fit.
8. **Schedule** — what day/time and timezone? _Default:_ Mondays 9:00 AM, cron `0 9 * * 1`, ask their timezone.

Don't collect secrets in chat — accounts are connected via OAuth in step 4 below.

## 3. Write the answers back

Persist everything — confirm before writing:

- **CLAUDE.md** — append the durable context under `## Your context`: name/role, Slack channels, CRM +
  record types, delivery channel, thresholds, exclusions, the final `pattern_guidance`, and the schedule.
  Do not touch the general instructions above it.
- **config.json** — mirror the structured settings (slack_channels, crm_name, crm_object_focus,
  output_channel, min_repeat_threshold, lookback_days, exclude_keywords, schedule, timezone).
- **Connected accounts** — walk the user through connecting **Slack** and their **CRM**. Confirm first.
- **.env** — only if a CRM needs an API key not covered by OAuth; copy from `.env.example` and have the
  user fill it in. Never echo secret values.

## 4. Schedule the run

With the user's confirmation, schedule the weekly run at their chosen day/time/timezone (default cron
`0 9 * * 1`).

## 5. Verify

- Confirm `config.json` and `## Your context` were written and Slack + CRM authenticate.
- Run one small smoke test: "Scan only the last 2 days and return whatever you find, even below the
  repeat threshold," and confirm a post lands in the delivery channel.

## 6. Done

Summarize what you configured, what the agent will now do each week, and how to give it its first task.
Tell the user they can re-run `agent-onboarding` anytime to reconfigure.
