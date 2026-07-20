---
name: agent-onboarding
description: 'First-run setup for Stale Deal Alert. Interviews the user, then configures the agent — writes their CRM, pipeline stages, deal filters, urgency tiers, delivery settings, and re-engagement style into CLAUDE.md and config.json, connects the CRM and Slack, and schedules the daily run. Runs automatically the first time the agent is imported.'
---

# Onboard Stale Deal Alert

You are helping a new user set up **Stale Deal Alert** for the first time. Be warm and brief. Ask a few
questions at a time, accept defaults quickly, and **confirm before any outward or destructive action**
(connecting accounts, writing files, scheduling jobs).

## 1. Welcome

Tell the user in one or two sentences: this agent checks their CRM every weekday morning for open deals
with no recent activity, tiers them by urgency, and posts a Slack alert with a suggested re-engagement
move for each one. Say you'll ask a few questions to set it up, and that the most important step is
mapping their CRM's exact stage names.

## 2. Interview

Ask these, grouped. Keep only answers that change behavior; offer the defaults shown.

1. **About you** — name, role, and the team/domain you work in.
2. **Your CRM** — which CRM (Salesforce, HubSpot, Pipedrive, …)?
3. **Pipeline stages** — this is the step people get wrong, so slow down here.
   - `active_stages`: which stages should I monitor for staleness? They must match your CRM's stage
     names **exactly**, including capitalization and spaces — have the user copy/paste from their CRM.
     _Starter:_ Discovery, Proposal, Negotiation, Verbal Commit.
   - `exclude_stages`: which stages should I always skip? _Starter:_ Closed Won, Closed Lost, On Hold,
     Prospecting (too early to go stale).
4. **Deal filters** —
   - `stale_threshold_days`: flag deals with no activity beyond this many days _(default 7)_.
   - `min_deal_value`: only alert on deals above this value _(default 0 = all deals)_.
   - `owner_filter`: `"me"` (only your deals), `"team"` (all reps on your team), or a specific list of
     rep names _(default "me" — expand to team once verified)_.
5. **Urgency tiers** — deals are bucketed by how stale they are. All three must be set, and Red > Orange
   > Yellow. _Defaults:_ `tier_yellow_days` 7 (worth a check-in), `tier_orange_days` 14 (needs attention
   soon), `tier_red_days` 21 (at risk). Suggest they match these to their own cycle length.
6. **Delivery** —
   - `output_channel`: which Slack channel should alerts post to? _(e.g. #deal-alerts)_
   - `tag_owner`: @mention the deal owner in Slack? _(default true)_
   - `include_suggested_action`: have me draft a re-engagement move per deal? _(default true)_
7. **Your re-engagement style (`reengagement_style`)** — in their own words, how do they like to
   re-engage stale deals? The agent uses this to draft each suggestion, so the more concrete the better.
   Give them a concrete starter to react to and edit, e.g.: _"I prefer re-engagement that references
   something specific — company news, a prior conversation point, a relevant insight — never a generic
   'just following up.' My go-to: find one new piece of information about their company (news, a job
   post, a LinkedIn update) and use it as a reason to reach out. If I can't find a specific hook, I'd
   rather call than email."_ Have them rewrite it in their own voice.
8. **Schedule** — what day/time and timezone? _Default:_ weekdays at 7:00 AM, cron `0 7 * * 1-5`, ask
   their timezone _(e.g. America/New_York)_.

Don't collect secrets in chat — accounts are connected via OAuth in step 4 below.

## 3. Write the answers back

Persist everything — confirm before writing:

- **CLAUDE.md** — append the durable context under `## Your context`: name/role, CRM, active/exclude
  stages, deal filters, urgency tiers, delivery settings, the final `reengagement_style`, and the
  schedule. Do not touch the general instructions above it.
- **config.json** — mirror the structured settings: `crm_name`, `active_stages`, `exclude_stages`,
  `stale_threshold_days`, `min_deal_value`, `owner_filter`, `tier_yellow_days`, `tier_orange_days`,
  `tier_red_days`, `output_channel`, `tag_owner`, `include_suggested_action`, `schedule`, `timezone`.
- **Connected accounts** — walk the user through connecting their **CRM** and **Slack**. Confirm first.
  Make sure the CRM identifies them with the same email/username they used to connect, so `owner_filter:
  "me"` resolves correctly.
- **.env** — only if their CRM needs an API key not covered by OAuth; copy from `.env.example` and have
  the user fill it in. Never echo secret values.

## 4. Schedule the run

With the user's confirmation, schedule the daily run at their chosen day/time/timezone (default cron
`0 7 * * 1-5`).

## 5. Verify

- Confirm `config.json` and `## Your context` were written and that the CRM + Slack authenticate.
- Run one small smoke test: "Run your stale deal check but set the threshold to 1 day and return the raw
  list of deals and their last activity dates before applying any filters — don't post to Slack, just
  show me here." Confirm the deals and dates look right before trusting the live run.

## 6. Done

Summarize what you configured, what the agent will now do each morning, and how to give it its first
task. Remind the user that the most common setup mistake is mismatched stage names, and that they can
re-run `agent-onboarding` anytime to reconfigure.
