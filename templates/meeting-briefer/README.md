> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/productivity-internal-ops/meeting-briefer)** — one-click deploy, no setup.

# Meeting Briefer

> Detects upcoming external meetings and posts a per-meeting brief — who they are, what's open, what changed since last touch, and recommended asks.

## What it does

Meeting Briefer runs hourly, scans your calendar, and posts a brief to Slack one hour before each qualifying external meeting. The brief covers who's attending (CRM context, email history, LinkedIn signals), what's unresolved between you, what's changed since the last touch, and 2–4 specific recommended asks in your voice. Unlike Morning Brief's daily sweep, Meeting Briefer is event-triggered — one brief per meeting, timed to land when it's actually useful.

Works for sales, CS, recruiting, VCs, founders — anyone who needs meeting context on demand rather than in a daily batch.

## What you'll need

- **Accounts:** Google Calendar or Outlook, Gmail or Outlook, CRM (optional but recommended), call notes source like Granola or Gong (optional), Slack
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** 2–3 example asks you've actually used in meetings (these make the recommended asks sound like you)

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - Your name, role, and the primary type of meetings you have
   - Which calendar and email to connect
   - Your company's internal domains (so internal meetings are skipped)
   - Which CRM to pull context from (optional)
   - Which meetings should get briefs (all external, keyword filter, or 3+ attendees)
   - 2–3 example recommended asks in your voice
   - Where to post briefs and how far before the meeting
3. Once setup finishes, give the agent its first task: `"Look at my next 24 hours and tell me which meetings you'd brief — don't post anything yet."`

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's instructions.
- `.claude/skills/agent-onboarding/` — first-run setup interview.

## Notes

- Briefs fire once per meeting, tracked between runs so they don't repeat.
- Sensitive meetings (configurable keyword list: board, legal, etc.) get minimal briefs — attendee list only, no CRM or email context pulled.
- LinkedIn enrichment uses browser control and may be slow or unavailable on locked profiles — it's optional.
- Default: `0 * * * *` (hourly), briefs post 60 minutes before each qualifying meeting.

Relevant subsegments: RVTK, MTTK, CSTK, CYBR, DEVT, DATA, AICO, FNTK, INSR, HRTK, LGTK, PPTK, SCTK, ECTK, SAAS, EDTK, CLTK, HLTK, MKTG, PRCM, MGMT, RECR, CRE, RESI, IBMA, PEVC
