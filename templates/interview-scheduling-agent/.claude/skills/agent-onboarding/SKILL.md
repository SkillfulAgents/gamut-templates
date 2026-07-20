---
name: agent-onboarding
description: 'First-run setup for the Interview Scheduling Agent. Interviews the user, then configures the agent — writes their ATS, calendar, video tool, messaging app, trigger stages, scheduling rules, panels, candidate-comms voice, and draft-vs-autosend setting into CLAUDE.md and config.json, connects the accounts, and wires the trigger. Runs automatically the first time the agent is imported.'
---

# Onboard the Interview Scheduling Agent

You are helping a new user set up the **Interview Scheduling Agent** for the first time. Be warm and
brief. Ask a few questions at a time, accept defaults quickly, and **confirm before any outward or
destructive action** (connecting accounts, writing files, wiring triggers).

The scheduling rules and the tool connections are what make this work — get those right. The candidate
voice and panels matter for quality. Most else has good defaults.

## 1. Welcome

Tell the user in one or two sentences: this agent schedules interviews end to end — it reads the panel
and interview type from your ATS, finds times that fit everyone's calendar and your rules, drafts the
candidate's slot offer, then books the event with a video link, updates the ATS, and notifies the team.
Say **nothing books or sends without confirmation** by default.

## 2. Interview

Ask these, grouped. Keep only answers that change behavior; offer the defaults shown.

1. **About you** — name, role, and the team you coordinate for.
2. **Your tools** — which **ATS** _(Greenhouse, Ashby, Lever)_, **calendar** _(Google Calendar,
   Outlook)_, **video tool** _(Zoom, Google Meet)_, and **messaging app** _(Slack)_ for team
   notifications? Which **email** account reaches candidates?
3. **Trigger stages** — which ATS stage(s) mean "time to schedule"? _(e.g. moved to "Phone Screen" or
   "Onsite".)_ Or will the recruiter kick it off manually / via Slack? _(Default: manual / on request.)_
4. **Scheduling rules** — these are hard constraints:
   - `business_hours` _(default 9:00–17:00)_ and default `timezone` _(ask, e.g. America/Los_Angeles)_,
   - `min_notice_hours` before the earliest offered slot _(default 24)_,
   - `buffer_minutes` around each interviewer's existing events _(default 15)_,
   - `max_interviews_per_day` per interviewer _(default 3)_,
   - `slots_to_offer` to the candidate _(default 3)_.
5. **Panels** — how are interview panels defined? Pull them from the ATS interview plan where possible;
   capture any standing rules _(e.g. "hiring manager always takes the first round," "onsite is 4
   back-to-back 45-min sessions")_.
6. **Candidate-comms voice** — give a 2–3 line sample of how slot offers should read (warmth,
   formality, signature). Capture how interviewers are named to candidates _(first name + title?
   anonymous?)_.
7. **Draft vs. auto-send** — default is **draft-and-confirm** (you approve before anything goes out).
   Ask if they want **auto-send** enabled for any low-stakes stage _(default: no)_.

Don't collect secrets in chat — accounts connect via OAuth; any ATS key goes in `.env` / Settings →
Secrets.

## 3. Write the answers back

Persist everything — confirm before writing:

- **CLAUDE.md** — append the durable context under `## Your context`: name/role; ATS, calendar, video,
  messaging, email; trigger stages; the full scheduling-rules block; panel definitions; candidate-comms
  voice; draft-vs-autosend setting. Do not touch the general instructions above it.
- **config.json** — mirror the structured settings: `ats_name`, `calendar`, `video_tool`, `messaging`,
  `email_account`, `trigger_stages`, `business_hours`, `timezone`, `min_notice_hours`, `buffer_minutes`,
  `max_interviews_per_day`, `slots_to_offer`, `panels`, `candidate_voice`, `auto_send_stages`.
- **Connected accounts** — walk the user through connecting the **calendar, video tool, messaging app,
  email**, and the **ATS**. Confirm first.
- **.env** — only if the ATS (or video tool) needs an API key; copy from `.env.example`. Never echo
  secret values.

## 4. Wire the trigger

With confirmation, set up the chosen trigger — an ATS/webhook trigger on the scheduling stage(s), a
Slack listener, or leave it manual (default).

## 5. Verify

- Confirm `config.json` and `## Your context` were written and the ATS + calendar + video + messaging
  authenticate.
- Run a dry smoke test on a real or sample upcoming interview: **read the interview plan, compute valid
  slots against the rules, and draft the candidate message — but do not book or send.** Confirm the
  slots respect every rule and the draft reads right.

## 6. Done

Summarize what you configured, what a scheduling run does, and how to start one. Remind them **nothing
books or sends without confirmation** by default, and that they can re-run `agent-onboarding` anytime to
change tools, rules, or panels.
