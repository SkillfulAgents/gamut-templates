> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/productivity-internal-ops/pre-event-dinner-briefing)** — one-click deploy, no setup.

# Pre-Event Dinner Briefing

> Makes sure your execs sit down at the dinner already knowing the room.

## What it does

The afternoon before a sales dinner or executive event, this agent scans your calendar for qualifying
events, pulls the confirmed external attendees, and researches each one against your CRM, call
recordings, email history, and the web. It posts a tight per-attendee briefing to Slack — deal stage,
last-call topics, current spend, expansion angle, and any intel worth knowing — where account owners
review and confirm context before they walk into the room.

## What you'll need

- **Accounts:** a CRM (Salesforce, HubSpot, or similar), a call recorder (Gong, Chorus, Fireflies,
  Otter), a calendar (Google Calendar or Outlook), Slack, and email (Gmail or Outlook, recommended).
- **API keys:** none by default (accounts connect via OAuth). See `.env.example` if your CRM or call
  recorder needs a key.
- **Other:** a Slack channel your account owners actually check before events.

## Getting started

1. Import this template into Gamut (drag the zip into the agent import dialog, or install it from the marketplace).
2. On import, a setup session starts automatically. The **agent-onboarding** skill will ask you:
   - Which CRM, call recorder, calendar, and email to use
   - The keywords in your event invite titles, how many days ahead to scan, and your company domain
   - Which Slack channel to post briefings to
   - Your briefing methodology (the most important part) and the intel areas always worth flagging
   - Your schedule (default: daily at 4:00 PM)
3. Once setup finishes, give it a first task, e.g.: *"Scan the calendar for the next 3 days and list any qualifying dinner or event invites with their external attendees — don't run the full research yet."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's role and method (find events → research attendees → build briefs → post to Slack), plus the exact output format.
- `.claude/skills/agent-onboarding/` — the first-run setup interview.
- `.env.example` — environment variables, if a system requires a key.

## Notes

- **No briefing posted even though you have a dinner tomorrow?** Your `event_keywords` don't match how the invite is titled — the agent does a substring match, so "exec dinner" won't catch "Executive Dinner." Add the exact phrase as it appears in your calendar.
- **Briefs are thin — many sections say "no data"?** CRM company names probably don't match attendee email domains ("Acme Corp" won't resolve to `acme.io`). Verify each account has the correct email domain in your CRM.
- **The briefing feels generic, not like your team's voice?** Your `briefing_style` needs specific, concrete guidance — add 1–2 examples of a good bullet. "$240K ARR, 2 BU expansion on the table in Q3" beats "a customer with room to grow."
- **Call recorder is missing recent calls?** Most recorders take 12–24 hours to process transcripts. For last-minute dinners, the agent falls back to CRM call notes.
- **A briefing fires for an internal planning meeting named "dinner"?** The agent skips events with no external attendees, but a vendor meeting with outside guests may still qualify. Rename the invite or add an exclusion phrase in CLAUDE.md.
- **A large customer event produces a wall of text?** The agent caps large groups at the 6 most senior attendees and lists the rest by name. Adjust that rule in CLAUDE.md if you want a different cap or seniority filter.
