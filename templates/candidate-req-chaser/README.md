> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/recruiting-hr/candidate-req-chaser)** — one-click deploy, no setup.

# Candidate & Req Pipeline Chaser

> Flags stale candidates, scheduling gaps, client submittal follow-ups, and contractor bench alerts — so recruiters spend their mornings acting, not ATS-staring.

**Relevant subsegments: RECR**

## What it does

Every weekday morning, Candidate & Req Pipeline Chaser scans your ATS for four types of pipeline
friction:

- **Stale candidates** — no stage movement or activity in 5+ business days (configurable), tiered by
  urgency (🟡 Watch, 🟠 Needs Attention, 🔴 Critical).
- **Scheduling gaps** — interview-scheduling requests (recruiter screen, onsite, technical panel, etc.)
  still outstanding after 3+ business days with no confirmed calendar event.
- **Client submittal follow-ups** (staffing/RPO mode) — candidates submitted to clients with no
  acknowledgment or feedback in 3+ business days.
- **Bench / redeploy alerts** (contractor mode) — contractors whose assignment end date is within 30
  days and who have no extension or new placement logged yet.

Each flagged item optionally comes with a short, recruiter-voice nudge draft — a suggested email
subject + one-liner, or a call talking point — so you know exactly what to do next. The agent posts
a daily digest to a Slack channel you choose, and (optionally) sends outbound nudge emails directly
from Gmail with your confirmation.

Works with Greenhouse, Ashby, Bullhorn, or any ATS with an API or connected account.

## What you'll need

- **ATS:** Greenhouse, Ashby, Bullhorn, or equivalent (API key or OAuth depending on the system).
- **Slack:** a channel for the daily digest (e.g. `#recruiting-digest`).
- **Gmail (optional):** only needed if you want the agent to send outbound nudge emails on your behalf.
- **Your ATS stage names:** copy/paste them exactly from your ATS during setup — capitalization and
  spaces matter.

## Getting started

1. Import this template into Gamut (drag the zip into the agent import dialog, or install from the
   marketplace).
2. A setup session starts automatically. The **agent-onboarding** skill will ask you:
   - Your name, team/firm, and role type (in-house recruiter, staffing agency, RPO, exec search,
     contractor desk, or combined)
   - Which ATS you use and how to connect it
   - Which pipeline stages to monitor and which to always skip (exact names matter — copy/paste from
     your ATS)
   - Staleness threshold in business days (default: 5), scheduling gap threshold (default: 3)
   - Staffing mode: client submittal follow-up window (default: 3 business days)
   - Contractor mode: bench alert window in calendar days (default: 30)
   - Slack channel for the daily digest and optional urgent-escalation contact
   - Whether to tag assigned recruiters, draft nudges, and/or send nudge emails via Gmail
   - Your nudge style (so drafts sound like you), and your preferred run schedule
3. Once setup finishes, run the smoke test it offers: *"Pull the first five candidates in my monitored
   stages and show me their stage and last activity date — don't post to Slack yet."*

First task to try after setup:

> **"Show me all candidates who haven't moved in 5+ days and draft nudges for the top 10."**

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's role, daily run method, and your configured context (filled in during
  onboarding).
- `.claude/skills/agent-onboarding/` — the first-run setup interview.
- `.env.example` — environment variables for ATS systems that require an API key.

## Troubleshooting

- **No alerts but you know candidates are stale?** Your `monitor_stages` entries likely don't match
  your ATS exactly — capitalization, trailing spaces (e.g. "Phone Interview " vs "Phone Interview"),
  or renamed stages will break the match. Copy/paste from your ATS.
- **Scheduling gaps not showing?** The ATS may log interview requests as activities, not as a
  separate scheduling object. During onboarding or by re-running `agent-onboarding`, describe how
  your ATS surfaces scheduling requests so the agent knows where to look.
- **Nudges feel generic?** Your `nudge_style` needs more specifics — add two or three concrete
  examples of follow-ups that worked and what made them land.
- **Recruiters not being @mentioned?** Slack handles aren't resolving from ATS user records. Either
  align ATS user emails with Slack emails, or accept plain-name fallback and update
  `escalation_slack_user` manually in `config.json`.
- **Bench alerts firing too early or too late?** Adjust `bench_alert_days` in `config.json` or re-run
  `agent-onboarding` to update the window.
