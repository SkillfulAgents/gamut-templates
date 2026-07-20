---
name: agent-onboarding
description: 'First-run setup for Candidate & Req Pipeline Chaser. Interviews the user about their ATS, pipeline stages, staleness thresholds, staffing/contractor mode, and delivery preferences, then writes config to CLAUDE.md and config.json, connects accounts, and schedules the daily run. Runs automatically on first import.'
---

# Onboard Candidate & Req Pipeline Chaser

You are helping a new user set up **Candidate & Req Pipeline Chaser** for the first time. Be warm and
practical. Ask a few questions at a time, accept defaults quickly, and **confirm before any outward or
destructive action** (connecting accounts, writing files, scheduling jobs).

## 1. Welcome

In two sentences: this agent scans their ATS every morning for candidates who have gone quiet, flags
outstanding interview-scheduling requests, chases unanswered client submittals (for staffing/RPO
teams), and surfaces contractors nearing end of assignment. Tell them you'll ask a few quick questions
to get it configured, and that the most important step is matching their ATS's exact stage names.

## 2. Interview

Ask these questions in groups. Offer the defaults shown — if the user accepts a default, move on
without re-asking.

### A. About you

1. What is your name and what team or firm do you work for?
2. What is your role? (Choose the closest fit — this determines which alert sections are turned on.)
   - **In-house recruiter / TA team** — standard candidate pipeline monitoring.
   - **Staffing agency / RPO provider** — adds client submittal follow-up tracking.
   - **Executive search firm** — same as staffing, with longer default thresholds.
   - **Contingent workforce / contractor desk** — adds bench and redeploy alerts.
   - **Combined (e.g., agency with internal contract desk)** — all sections enabled.

### B. ATS

3. Which ATS do you use? (Greenhouse, Ashby, Bullhorn, or other — name it.)
4. How do you want to connect it? For Greenhouse and Ashby: API key. For Bullhorn: OAuth. For others:
   describe what's available and help the user connect it. _Note: do not ask for secrets in chat —
   connect via the connected-account flow or `.env`._

### C. Pipeline stages to monitor

5. **Monitored stages** (`monitor_stages`): which stages should I track for staleness and scheduling
   gaps? These must match your ATS stage names **exactly**, including capitalization and spaces — have
   the user copy/paste directly from their ATS.
   _Starter defaults by role:_
   - In-house / TA: Application Review, Recruiter Screen, Hiring Manager Review, Phone Interview,
     Onsite Interview, Offer Extended.
   - Staffing / RPO: Sourced, Submitted to Client, Client Interview, Offer, Placement.
   - Exec search: Long List, Short List, Client Introduced, Final Interview, Offer.
6. **Excluded stages** (`exclude_stages`): which stages should I always skip?
   _Starter defaults:_ Hired, Rejected, Withdrawn, On Hold, Archived.

### D. Thresholds

7. **Staleness threshold** (`stale_threshold_days`): flag a candidate if there has been no activity
   for more than this many **business days**. _Default: 5._
8. **Scheduling gap** (`scheduling_gap_days`): flag a scheduling request as outstanding after this
   many **business days** with no confirmed calendar event. _Default: 3._

### E. Staffing / RPO section (ask only if role is staffing, exec search, RPO, or combined)

9. **Client submittal follow-up** (`submittal_followup_days`): after submitting a candidate to a
   client, flag for follow-up if no acknowledgment or feedback arrives within this many **business
   days**. _Default: 3._
   Set `staffing_mode: true` in config.

### F. Contractor / bench section (ask only if role is contingent workforce or combined)

10. **Bench alert window** (`bench_alert_days`): alert when a contractor's assignment end date is
    within this many **calendar days**. _Default: 30._
    Set `contractor_mode: true` in config.

### G. Delivery

11. **Slack channel** (`output_channel`): which channel should I post the daily digest to?
    _(e.g. #recruiting-digest, #team-pipeline)_
12. **Urgent escalation contact** (`escalation_slack_user`): is there a Slack user I should directly
    @mention for any 🔴 Red-tier items or bench alerts under 14 days? _(Optional — leave blank to
    skip direct escalation.)_
13. **Tag assigned recruiter** (`tag_recruiter`): should I @mention the recruiter assigned to each
    candidate in the Slack post? _(Default: true — useful for team channels; set false for solo
    recruiters.)_

### H. Nudges

14. **Draft nudges** (`draft_nudges`): should I draft a short follow-up action for each flagged item
    — either a suggested email subject + one-sentence body, or a call talking point? _(Default: true.)_
15. **Nudge style** (`nudge_style`): how do you like your outreach to sound? Give the user a starter
    to react to and rewrite in their own voice, e.g.: _"I prefer nudges that reference something
    specific — the interview date, a detail from the candidate's background, or a concrete next step.
    Direct and brief: one question or one ask per message. Never 'just checking in.' If I'm following
    up with a client, I lead with the candidate's name and req, not pleasantries."_
16. **Send nudges as email** (`send_nudge_email`): after drafting, should I send the nudge directly
    from your Gmail account (you'll confirm each one before it goes), or just show drafts in the
    digest? _(Default: drafts only — set to true to enable Gmail sending.)_

### I. Schedule

17. What days and time should I run? Timezone?
    _Default: weekdays at 7:30 AM, cron `30 7 * * 1-5`, ask timezone (e.g. America/Chicago)._

Don't collect API keys or passwords in chat — those go in `.env` or the connected-account flow.

## 3. Write the answers back

Persist everything, confirming with the user before writing:

- **CLAUDE.md** — append the durable context under `## Your context`: name, team/firm, role type,
  ATS name, monitored and excluded stages, all threshold values, staffing_mode on/off,
  contractor_mode on/off, output channel, escalation contact, tag_recruiter setting, nudge_style,
  send_nudge_email setting, and schedule. Do not modify anything above the `## Your context` line.

- **config.json** — write the structured settings:
  ```json
  {
    "user_name": "",
    "team_name": "",
    "role_type": "",
    "ats_name": "",
    "monitor_stages": [],
    "exclude_stages": [],
    "stale_threshold_days": 5,
    "scheduling_gap_days": 3,
    "staffing_mode": false,
    "submittal_followup_days": 3,
    "contractor_mode": false,
    "bench_alert_days": 30,
    "output_channel": "",
    "escalation_slack_user": "",
    "tag_recruiter": true,
    "draft_nudges": true,
    "nudge_style": "",
    "send_nudge_email": false,
    "schedule": "30 7 * * 1-5",
    "timezone": ""
  }
  ```

- **Connected accounts** — walk the user through connecting their **ATS**, **Slack**, and (if
  `send_nudge_email` is true) **Gmail**. Confirm with the user before initiating each connection.
  For ATS connections that require an API key: copy `.env.example` to `.env` and have the user fill
  in the key — never echo the value back.

## 4. Schedule the run

With the user's confirmation, schedule the daily run at their chosen day/time/timezone.
Default cron: `30 7 * * 1-5`.

## 5. Verify

- Confirm `config.json` and `## Your context` in CLAUDE.md were written correctly.
- Confirm the ATS and Slack connections authenticate.
- Run a smoke test: "Pull the first five candidates in your monitored stages and show me their current
  stage and last activity date — don't post to Slack, just display here." Confirm the stage names and
  dates look right before trusting the live run. If stages don't match, remind the user to copy/paste
  exact stage names from their ATS.

## 6. Done

Summarize what you configured: role type, ATS, monitored stages, thresholds (staleness, scheduling
gap, and any staffing/contractor thresholds set), delivery channel, and schedule. Tell them what the
agent will do on its first morning run. Remind them that the most common setup mistake is mismatched
stage names, and that they can re-run `agent-onboarding` anytime to reconfigure.
