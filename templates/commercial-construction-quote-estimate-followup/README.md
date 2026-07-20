> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/quote-estimate-follow-up/commercial-construction-quote-estimate-followup)** — one-click deploy, no setup.

# Commercial Construction/GC - Quote / Estimate Follow-up

Estimators at commercial GCs submit dozens of bids and then lose track of them once the proposal is out. Prospects go quiet, bids expire, and the team never finds out why they lost — or fails to follow up on bids that would have converted with one more touchpoint. This agent tracks every open bid and estimate, follows up with silent prospects on a consistent schedule, flags expiring bids before they lapse, and maintains the win-rate data the estimating team needs to improve close rates.

## Who this is for

Estimators, business development reps, and operations leads at commercial GCs who submit a high volume of bids and want systematic follow-up without manual tracking.

Relevant subsegments: GCON

Best fit for GCs running 20+ open bids at a time in Procore, Sage/Viewpoint, or a CRM.

## What it does

1. **Open bid tracking** — pulls all open bids and estimates from the connected system daily, tracking project name, owner, value, submission date, and expiration date
2. **Silent prospect identification** — flags any prospect who has exceeded the configured follow-up window without a reply or status update
3. **Automated follow-up** — drafts and sends a project-specific follow-up email from the assigned estimator; queues for rep review above the configured high-touch threshold
4. **Expiration alerts** — alerts the estimator via Slack for any bid expiring within the configured warning window
5. **Win-rate reporting** — generates weekly or monthly summaries of win rate by rep, project type, and value band, and tracks average days to decision

## Key integrations

- **Procore / Sage / Viewpoint** — bid and estimate records, project data
- **Salesforce / HubSpot / spreadsheet** — CRM pipeline for tracking outcomes
- **Gmail / Outlook** — follow-up email delivery
- **Slack** — expiration alerts, win-rate digests, escalations

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your bid system, follow-up preferences, high-touch threshold, and reporting setup
3. Give the agent its first task: *"Check all open bids and follow up with anyone who hasn't responded in the past [N] days."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`.

## Pattern

Vertical / NON-TECH - Commercial construction and general contractors

Relevant subsegments: GCON
