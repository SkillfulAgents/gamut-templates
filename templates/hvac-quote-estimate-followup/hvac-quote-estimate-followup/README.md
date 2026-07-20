# HVAC/Plumbing/Electrical - Quote / Estimate Follow-up

HVAC, plumbing, and electrical contractors send dozens of estimates every week and lose booked revenue simply because no one followed up. This agent monitors every open estimate in ServiceTitan or FieldEdge, sends owner-voiced follow-up messages that escalate naturally as time passes, flags proposals approaching their expiration date, and delivers a weekly win-rate report so the owner knows exactly where the pipeline stands.

## Who this is for

Owner-operators and office managers at HVAC, plumbing, or electrical contracting businesses who send estimates regularly, have no dedicated sales coordinator to track follow-ups, and want a consistent process for staying in front of prospects without the owner manually chasing every open quote.

Relevant subsegments: HVAC

Best fit for contractors sending 10–100+ estimates per month across service calls, installs, and project work.

## What it does

1. **Pull & categorize open estimates** — pulls open proposals from ServiceTitan or FieldEdge, organizes by status (awaiting response, viewed, follow-up attempted, expiring soon, expired), and flags any estimate that has been open past the configured follow-up window
2. **Prioritize outreach** — sorts open estimates by job value and age, checks contact history for each prospect, and determines the correct follow-up step (first nudge, second check-in, expiration notice, or expired re-quote offer)
3. **Draft & send follow-up messages** — writes all outreach in the owner or estimator's voice, referencing the specific job type and scope; escalates in tone as estimates age; sends by email by default with SMS as an option
4. **Flag expiring estimates** — scans every morning for estimates expiring within the warning window, alerts the owner with a prioritized list, and queues expiration-warning messages for review or auto-send
5. **Track responses & update pipeline** — logs every outcome (won, lost, more info requested) in the pipeline tracker, marks jobs as won in the system when accepted, and captures decline reasons for analysis
6. **Win-rate & pipeline report** — delivers a weekly summary of open estimate value, win rate (overall and by job type), average days to decision, and top open opportunities

## Key integrations

- **ServiceTitan** — field service management, estimate and job tracking, contact history
- **FieldEdge** — alternative FSM platform for estimate management and dispatch scheduling
- **Email** — primary channel for prospect follow-up outreach
- **SMS** — optional follow-up channel for prospects who provided a mobile number
- **Slack** — owner alerts and weekly pipeline digest (optional)

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your trade type, FSM system, estimator name, follow-up timing preferences, and reporting destination
3. Give the agent its first task: *"Show me all open estimates older than 5 days and draft a follow-up message for each one."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`. Edit either file to update follow-up timing windows, estimate expiration thresholds, the estimator name used for sign-offs, outreach channels, or the reporting cadence and destination.

## Pattern

Vertical / NON-TECH — HVAC, plumbing, and electrical contracting sales ops
