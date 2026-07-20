> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/recruiting-hr/interview-scheduling-agent)** — one-click deploy, no setup.

# Interview Scheduling Agent

> Turns "this candidate is ready to interview" into a booked, video-linked, ATS-updated, team-notified interview — without a recruiter playing calendar tetris.

## What it does

When a candidate is ready for an interview, the agent:

1. Picks up the request (an ATS stage change, a Slack ping, or a direct ask).
2. Reads the **interview plan** from your ATS — who's on the panel, the interview type, the duration.
3. Finds times that work by reading the panel's calendars and honoring **every** scheduling rule:
   business hours, timezone, minimum notice, buffers, no double-booking, and per-interviewer daily
   limits.
4. Drafts a warm, concise **candidate-facing slot offer** (your voice, with timezone).
5. On confirmation, **books the calendar event**, invites the panel + candidate, attaches the **video
   link** (Zoom/Meet), updates the **ATS** to the scheduled state, and **notifies the team**.
6. Handles the messy parts — declines, conflicts that appear after the offer, and reschedules.

Nothing books or sends without a confirmation — proposing is automatic, committing is a decision.

## Fully configurable

You set these during onboarding; the workflow stays the same:

- **ATS** — Greenhouse, Ashby, Lever, or similar.
- **Calendar** — Google Calendar, Outlook.
- **Video** — Zoom, Google Meet.
- **Messaging** — Slack (or wherever your team lives) for notifications.
- **Scheduling rules** — business hours, timezone, minimum notice, buffers, daily interview limits,
  how many slots to offer.
- **Trigger stages** — which ATS stages kick off scheduling.
- **Panels & candidate-comms voice**, and **draft-vs-auto-send** per stage.

## What you'll need

- **Accounts:** your ATS, a calendar, a video tool, a messaging app, and a connected email for
  candidate-facing messages.
- **API keys:** only if your ATS uses one (e.g. `GREENHOUSE_API_KEY`) — see `.env.example`. Calendar,
  video, email, and Slack connect via OAuth.

## Getting started

1. Import this template into Gamut (drag the zip into the agent import dialog, or install it from the
   marketplace).
2. On import, a setup session starts automatically. The **agent-onboarding** skill walks you through
   your ATS, calendar, video tool, messaging app, scheduling rules, panels, and trigger stages, then
   connects accounts.
3. Test it: *"Schedule the [stage] interview for [candidate] — show me the slots and the candidate
   message before anything goes out."*

## What's inside

- `CLAUDE.md` — the agent's role and method (read plan → find availability → offer → book → update ATS →
  notify), with the confirm-before-book guardrails.
- `.claude/skills/agent-onboarding/` — the first-run setup interview.
- `.env.example` — an ATS API key, if your ATS needs one.

## Notes

- **It never books or sends silently.** Default is draft-and-confirm; auto-send is opt-in per stage.
- **Scheduling rules are hard constraints** — if it can't find a valid slot, it tells you which rule to
  relax rather than booking a bad time.
- **Timezones are always explicit** in candidate messages — the most common scheduling bug, designed
  out.
- **Reschedules and cancellations are outward actions** — the agent confirms before moving anything on
  someone's calendar.
- **Pairs well with the Interview Prep Kit agent** — the scheduled event can carry the prep kit straight
  into the panel's invite.
