> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/productivity-internal-ops/morning-brief)** — one-click deploy, no setup.

# Morning Brief

> Pulls today's calendar, enriches external attendees with CRM and LinkedIn context, and drops a one-page brief in Slack before your first meeting.

## What it does

Morning Brief runs every weekday at 7 AM, pulls your calendar, looks up every external attendee in your CRM and email history, optionally enriches with LinkedIn context, and posts a single brief to Slack. The brief covers your meeting schedule, prep priorities, per-attendee context, recommended asks, and open pipeline signals — everything you need to walk into the day prepared, in 90 seconds of reading.

Works for anyone who has external meetings: sales, CS, recruiting, founders, VCs, and executive teams.

## What you'll need

- **Accounts:** Google Calendar or Outlook, Gmail or Outlook, CRM (optional), Slack
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** none

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - Your name, role, and how you want to frame every meeting
   - Which calendar and email to connect
   - Your company's internal domains (so internal-only meetings are skipped)
   - Which CRM to pull context from (optional)
   - Where to post the brief (Slack channel or DM)
   - Your preferred tone and focus signals (stalled deals, unanswered emails, etc.)
3. Once setup finishes, give the agent its first task: `"Run a dry-run brief for today — don't post to Slack."`

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's instructions.
- `.claude/skills/agent-onboarding/` — first-run setup interview.

## Notes

- The brief posts once per day. If there are no external meetings, it posts a short note with focus signals only.
- LinkedIn enrichment uses browser control and can be slow on locked profiles — it's optional and can be disabled during onboarding.
- Default schedule: `0 7 * * 1-5` in `America/New_York` — change your timezone in Gamut's task settings.

Relevant subsegments: ALL
