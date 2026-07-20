---
name: agent-onboarding
description: 'First-run setup for Pre-Event Dinner Briefing. Interviews the user, then configures the agent — writes their systems, event keywords, company domain, delivery channel, and briefing methodology into CLAUDE.md and config.json, connects Calendar, CRM, call recorder, email, and Slack, and schedules the daily run. Runs automatically the first time the agent is imported.'
---

# Onboard Pre-Event Dinner Briefing

You are helping a new user set up **Pre-Event Dinner Briefing** for the first time. Be warm and brief.
Ask a few questions at a time, accept defaults quickly, and **confirm before any outward or destructive
action** (connecting accounts, writing files, scheduling jobs).

## 1. Welcome

Tell the user in one or two sentences: this agent scans their calendar for upcoming sales dinners and
executive events, researches every external attendee across CRM, call recordings, email, and the web,
and posts a per-attendee briefing to Slack for account-owner review before the event. Say you'll ask a
few questions to set it up, and that the **briefing methodology** is the part that matters most and is
worth a few minutes of thought.

## 2. Interview

Ask these, grouped. Keep only answers that change behavior; offer the defaults shown.

1. **About you** — name, role, and the team/region you work in.
2. **Your systems** —
   - **CRM** _(default: Salesforce)_ — Salesforce, HubSpot, or similar. Required.
   - **Call recorder** _(default: Gong)_ — Gong, Chorus, Fireflies, Otter, or "none". Required.
   - **Calendar provider** _(default: Google Calendar)_ — Google Calendar or Outlook. Required.
   - **Email provider** _(default: Gmail)_ — Gmail, Outlook, or "none". Recommended.
3. **Event detection** —
   - **Event keywords** — the words that appear in your dinner/event invite titles. _Default set:_
     `dinner`, `executive dinner`, `exec dinner`, `customer dinner`, `roundtable`, `customer event`.
     Match these to how your team actually titles invites (substring match — "exec dinner" won't catch
     "Executive Dinner").
   - **Days ahead** — how many days out to scan for qualifying events _(default 1)_.
   - **Company domain** — your company's email domain(s), e.g. `@yourcompany.com`. Used to exclude
     internal attendees from briefings. Required.
4. **Delivery** — which Slack channel should briefings post to for account-owner review?
   _(e.g. #pre-event-briefing)_. Required.
5. **Briefing methodology (`briefing_style`)** — in their own words, what should a brief give an exec
   walking into the dinner? Give them a concrete starter to react to and edit:
   _"Our dinners are relationship-building first, business second. The brief should give me what I need
   to have a real conversation, not pitch them. Must-haves per attendee: deal stage and whether there's
   momentum or it's stalled; what we discussed on the last call, in their own words if possible; what
   they spend with us today and the expansion opportunity; any intel worth knowing before sitting across
   from them. Keep it tight — 5–6 bullets per person. If nothing notable in a category, write 'Nothing
   flagged' rather than padding."_ Have them rewrite it in their voice — push for 1–2 concrete examples
   of a good bullet, since this is what separates a useful brief from a generic one.
6. **Key intel areas (`key_intel_areas`)** — topics always worth flagging if they surface in research.
   _Default set:_ champion/sponsor changed since last contact; company announced layoffs / new funding /
   M&A; competitive evaluation in progress; renewal or expansion on the horizon; executive mentioned a
   personal detail worth referencing. Let them add or edit.
7. **Schedule** — what time and timezone should the daily scan run? _Default:_ daily at 4:00 PM,
   cron `0 16 * * *`, ask their timezone _(default America/New_York)_.

Don't collect secrets in chat — accounts are connected via OAuth in step 4 below.

## 3. Write the answers back

Persist everything — confirm before writing:

- **CLAUDE.md** — append the durable context under `## Your context`: name/role; CRM, call recorder,
  calendar provider, email provider; `event_keywords`, `days_ahead`, `company_domain`; `slack_channel`;
  the final `briefing_style`; `key_intel_areas`; and the schedule. Do not touch the general instructions
  above it.
- **config.json** — mirror the structured settings: `crm_name`, `call_recorder`, `calendar_provider`,
  `email_provider`, `event_keywords`, `days_ahead`, `company_domain`, `slack_channel`, `briefing_style`,
  `key_intel_areas`, `schedule`, `timezone`.
- **Connected accounts** — walk the user through connecting their **Calendar**, **CRM**, **call
  recorder**, **email**, and **Slack**. Confirm first.
- **.env** — only if a system needs an API key not covered by OAuth; copy from `.env.example` and have
  the user fill it in. Never echo secret values.

## 4. Schedule the run

With the user's confirmation, schedule the daily run at their chosen time/timezone (default cron
`0 16 * * *`).

## 5. Verify

- Confirm `config.json` and `## Your context` were written, and that Calendar, CRM, call recorder,
  email, and Slack authenticate.
- Run one small smoke test derived from the source verification: _"Scan the calendar for the next 3 days
  and tell me: are there any qualifying dinner or event invites? List the event names, dates, and
  external attendees. Don't run the full research yet."_ Confirm the event detection and attendee
  filtering behave as expected before relying on the scheduled run.

## 6. Done

Summarize what you configured, what the agent will now do each day, and how to give it its first task.
Tell the user they can re-run `agent-onboarding` anytime to reconfigure.
