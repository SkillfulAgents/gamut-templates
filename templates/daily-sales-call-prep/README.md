> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/sales-pipeline/daily-sales-call-prep)** — one-click deploy, no setup.

# Daily Sales Call Prep

> Turns a morning of scattered context-gathering into one sharp prep brief before your first meeting.

## What it does

Every weekday morning, this agent checks your calendar for the day's external meetings, then researches
each one across your email, CRM, call recordings, and the open web. It posts a single prep brief to a
Slack channel you choose — one block, before your first meeting. Each brief is tuned to your own selling
methodology: status quo signals, a cost-of-inaction angle, a conversational opening POV, and discovery
angles, all customized to how you sell.

## What you'll need

- **Accounts:** Calendar (Google Calendar or Outlook), Email (Gmail or Outlook), a CRM (Salesforce,
  HubSpot, Pipedrive, or similar), and Slack. Optionally a call recorder (Gong, Chorus, Fireflies, Otter).
- **API keys:** none by default (accounts connect via OAuth). See `.env.example` if your CRM or call
  recorder needs a key.
- **Other:** a Slack channel you actually check first thing in the morning, and 20–30 minutes for setup —
  the methodology sections take the most thought and are what make the output yours.

## Getting started

1. Import this template into Gamut (drag the zip into the agent import dialog, or install it from the marketplace).
2. On import, a setup session starts automatically. The **agent-onboarding** skill will ask you:
   - Which calendar, email, CRM, and call recorder you use
   - Your meeting filters (internal domains to skip, minimum duration, how many attendees to research)
   - Which Slack channel to post briefs to
   - Your call-prep methodology (status quo signals, COI framing, opening POV, discovery focus areas) — edit the starters into your own voice
   - Your schedule and timezone
3. Once setup finishes, run the verification test, e.g.: *"Run your call prep for today but just return the meeting list and attendees — don't do the full research yet. Tell me which meetings you'd prep for and which you'd skip."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's role and method (pull meetings → research → build brief → post).
- `.claude/skills/agent-onboarding/` — the first-run setup interview.
- `.env.example` — environment variables, if your CRM or call recorder requires a key.

## Notes

- **No brief posted but you have meetings today?** Check `exclude_internal_domains` — if your company's domain isn't listed exactly, every meeting gets filtered as internal. Also confirm the calendar integration can see external meetings; some permission scopes only return events you organized.
- **Briefs are vague even with good methodology fields?** The `status_quo_signals`, `coi_framing`, and `pov_style` fields need concrete examples of what good looks like. If yours are abstract ("I look for pain"), the output will be too. Rewrite with 2–3 specific scenarios you've seen work, with real numbers.
- **Briefs include obvious internal meetings (1:1s, standups)?** Your `exclude_internal_domains` list is incomplete or has typos — add every domain your company uses. Bump `min_meeting_duration_minutes` if your standups run 30 minutes.
- **Some meetings have great briefs, others say "No prior data available"?** Expected for new prospects. If you see it on accounts you know have history, check that the CRM company name matches the attendee's email domain — common mismatch: "Acme Corp" in CRM but emails come from "acme.io".
- **The COI angle keeps generating the same generic line?** Your `coi_framing` is too high-level. Add 1–2 worked examples with actual numbers from real deals — that gives the agent a pattern to follow.
