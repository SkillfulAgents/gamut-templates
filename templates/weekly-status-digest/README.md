> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/productivity-internal-ops/weekly-status-digest)** — one-click deploy, no setup.

# Weekly Status Digest

> Pulls your function's key metrics weekly, writes a narrative of what changed and why, and closes out last week's flagged risks.

## What it does

Weekly Status Digest runs every Monday morning, pulls the metrics you define from wherever they live, compares each one to a baseline you choose, writes a narrative explaining anomalies and wins, closes out last week's flagged risks, and posts one clean digest to Slack. It works for any function — recruiting, marketing, sales, ops, engineering, CS — and the same skeleton adapts to any audience level from IC to board.

## What you'll need

- **Accounts:** Data source systems (Salesforce, HubSpot, Greenhouse, Google Sheets, Looker, or other), storage (Google Drive or Notion), Slack
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** A list of the 4–8 metrics you want tracked and which system to pull each from

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - Your name and function
   - Which 4–8 metrics matter most and where to pull them from
   - Which systems to connect
   - Where to archive digests (so prior-week flags can be closed)
   - Where to post (Slack channel or DM)
   - Your audience level (IC/team, exec, or board) and narrative style
   - Your anomaly sensitivity threshold
3. Once setup finishes, give the agent its first task: `"Pull this week's metrics — just the raw numbers, don't write narrative or post anything."`

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's instructions.
- `.claude/skills/agent-onboarding/` — first-run setup interview.

## Notes

- The digest archives to your chosen storage on every run so flags from prior weeks can be properly closed out — without that storage connection the close-out step won't work.
- Default schedule: `0 8 * * 1` (Mondays at 8 AM Eastern) — change your timezone in Gamut's task settings.
- Anomaly threshold default is 25% change week-over-week — tune up for noisy metrics, down for more sensitivity.

Relevant subsegments: ALL
