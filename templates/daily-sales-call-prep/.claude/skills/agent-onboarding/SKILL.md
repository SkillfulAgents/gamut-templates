---
name: agent-onboarding
description: 'First-run setup for Daily Sales Call Prep. Interviews the user, then configures the agent — writes their systems, meeting filters, methodology, and delivery channel into CLAUDE.md and config.json, connects Calendar/Email/CRM/Slack (and a call recorder if used), and schedules the daily run. Runs automatically the first time the agent is imported.'
---

# Onboard Daily Sales Call Prep

You are helping a new user set up **Daily Sales Call Prep** for the first time. Be warm and brief. Ask
a few questions at a time, accept defaults quickly, and **confirm before any outward or destructive
action** (connecting accounts, writing files, scheduling jobs).

## 1. Welcome

Tell the user in one or two sentences: this agent checks their calendar each morning for the day's
external meetings, researches each one across email, CRM, call recordings, and the web, and posts a
single prep brief to Slack — tuned to their own selling methodology. Say you'll ask a few questions to
set it up, and flag that the methodology questions are the most important part and worth a few extra
minutes.

## 2. Interview

Ask these, grouped. Keep only answers that change behavior; offer the defaults shown.

**Your systems**
1. **About you** — name, role, and the team/domain you sell into.
2. **Calendar** — Google Calendar or Outlook? _(default: Google Calendar)_
3. **Email** — Gmail or Outlook? _(default: Gmail)_
4. **CRM** — which CRM (Salesforce, HubSpot, Pipedrive, …)? _(required)_
5. **Call recorder** — Gong, Chorus, Fireflies, Otter, or "none"? _(default: none)_

**Meeting filters**
6. **Internal domains** (`exclude_internal_domains`) — which email domains are your own company's, so
   internal-only meetings are skipped? _(e.g. @yourcompany.com — list all domains you use)_
7. **Minimum duration** (`min_meeting_duration_minutes`) — skip meetings shorter than this. _(default 20)_
8. **Attendees to research** (`max_attendees_to_research`) — for big meetings, how many of the most
   senior/relevant attendees to deep-research? _(default 3)_

**Delivery**
9. **Output channel** (`output_channel`) — which Slack channel should the briefs post to? _(e.g. #call-prep)_

**Your call-prep methodology** — this is what makes the briefs *yours*. For each of the next three,
give the user a concrete starter to react to and have them rewrite it in their own voice. Do not bake
these into CLAUDE.md — they live in the user's context and the agent applies them verbatim.

10. **Status quo signals** (`status_quo_signals`) — what evidence tells you a prospect is in an
    uncomfortable status quo? Starter to edit: _"I look for evidence the prospect is in an
    uncomfortable status quo — new CRO/VP Sales, publicly missed targets, hiring spikes in areas
    adjacent to our use case, competitive pressure in earnings or news, anything that suggests a
    burning-platform moment. I want specifics, not generalities — 'Q3 revenue missed by 12% per their
    earnings call,' not 'they've had some challenges.' Quote sources when possible."_
11. **Cost-of-inaction framing** (`coi_framing`) — how do you frame the cost of doing nothing? Starter
    to edit: _"COI = Cost of Inaction. I don't sell features — I sell the cost of doing nothing. For
    each prospect, connect their specific situation to what staying the course costs them in time,
    revenue, competitive risk, or opportunity cost. Be quantifiable where possible — 'every new rep on
    their current process ramps 30% slower, which at their hiring pace means X months of revenue lag,'
    not 'they'll lose business if they don't change.'"_
12. **Opening POV style** (`pov_style`) — how do you open a call? Starter to edit: _"I open with a 2–3
    sentence conversational POV — a hypothesis about their business that shows I've done homework and
    have a perspective, not just questions. It should sound like something you'd say to a peer before a
    meeting, not a press release. Warm, direct, slightly opinionated, no vendor-speak. Structure:
    '[observation about their situation]. I'm curious whether [implied challenge]. Wanted to start
    there.'"_
13. **Discovery focus areas** (`discovery_focus_areas`) — topics you always try to uncover. Offer this
    default list and let them edit: _who controls the budget (not just who's in the room); what they've
    already tried and why it didn't work; what happens if they do nothing for another 6 months; who
    else needs to be involved to decide; whether there's a real deadline or it's a nice-to-have._

**Schedule**
14. **Schedule** — what day/time and timezone should it run? _Default:_ weekdays 8:00 AM, cron
    `0 8 * * 1-5`; ask their timezone (e.g. America/New_York).

Don't collect secrets in chat — accounts are connected via OAuth in step 4 below.

## 3. Write the answers back

Persist everything — confirm before writing:

- **CLAUDE.md** — append the durable context under `## Your context`: name/role, calendar/email/CRM/
  call recorder, internal domains, the meeting filters, delivery channel, the final
  `status_quo_signals` / `coi_framing` / `pov_style` / `discovery_focus_areas`, and the schedule. Do
  not touch the general instructions above it.
- **config.json** — mirror the structured settings: `calendar_provider`, `email_provider`, `crm_name`,
  `call_recorder`, `exclude_internal_domains`, `min_meeting_duration_minutes`,
  `max_attendees_to_research`, `output_channel`, `discovery_focus_areas`, `schedule`, `timezone`. (The
  free-text methodology fields live in `## Your context`.)
- **Connected accounts** — walk the user through connecting **Calendar**, **Email**, **CRM**, **Slack**,
  and the **call recorder** if they use one. Confirm first.
- **.env** — only if the CRM or call recorder needs an API key not covered by OAuth; copy from
  `.env.example` and have the user fill it in. Never echo secret values.

## 4. Schedule the run

With the user's confirmation, schedule the daily run at their chosen time/timezone (default cron
`0 8 * * 1-5`).

## 5. Verify

- Confirm `config.json` and `## Your context` were written, and that Calendar, Email, CRM, Slack (and
  the call recorder, if any) authenticate.
- Run one small smoke test: _"Run your call prep for today but just return the meeting list and
  attendees — don't do the full research yet. Tell me which meetings you'd prep for and which you'd
  skip."_ Confirm the meeting list and internal/external filtering look right before relying on the
  full run.

## 6. Done

Summarize what you configured, what the agent will now do each morning, and how to give it its first
task. Remind the user that the methodology fields are what make the briefs theirs — they can re-run
`agent-onboarding` anytime to sharpen them or reconfigure anything else.
