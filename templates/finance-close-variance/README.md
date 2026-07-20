> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/finance-accounting/finance-close-variance)** — one-click deploy, no setup.

# Finance Close & Variance Digest

> Automates month-end close review: flags journal entry anomalies, writes variance commentary, and surfaces the exception narrative for the finance team.

## What it does

Finance Close & Variance Digest pulls your trial balance and JE activity at month-end, flags anomalies (unusual entries, large manual JEs, entries posted after cutoff, vague descriptions), computes variances for your key accounts vs your chosen baseline, writes variance commentary for each flagged account, and delivers an exception narrative the team can review before finalizing the close. Designed for Controllers and Finance Directors who want a faster, more consistent close review — without a junior analyst spending two days on a spreadsheet.

Distinct from Pack Builder (board decks) — this is close review and JE analysis, not investor reporting.

## What you'll need

- **Accounts:** GL/ERP (QuickBooks Online, Xero, NetSuite, Sage, or similar), document storage for archiving (Google Drive, Notion, or SharePoint), Slack or email for notifications
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** A list of the 4–10 key accounts to track for variance analysis

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - Your role and GL system to connect
   - Which key accounts to analyze
   - Variance baseline (prior period, budget, or prior year)
   - Variance threshold (% that triggers commentary)
   - Large JE threshold ($)
   - Where to save and post the exception narrative
3. Once setup finishes, give the agent its first task: `"Scan last month's JE activity for anomalies — list what you'd flag, don't write commentary yet."`

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's instructions.
- `.claude/skills/agent-onboarding/` — first-run setup interview.

## Notes

- Read-only analysis — this agent never writes back to the GL or adjusts any entry.
- If the GL system isn't connected or the period isn't closed, the agent stops and alerts rather than analyzing partial data.
- Default schedule: last business day of the month, or triggered on-demand.

Relevant subsegments: ALL
