> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/job-project-status/commercial-construction-job-project-status)** — one-click deploy, no setup.

# Commercial Construction/GC - Job / Project Status

The morning ops meeting should not start with 20 minutes of data gathering. This Gamut agent connects to Procore and your accounting system each morning, checks every active job against schedule, budget, open RFIs, sub milestones, and procurement risk, and delivers a prioritized brief before the day starts. Critical items surface first. On-track projects get a clean bill of health so the principal knows coverage is complete.

## Who this is for

General contractors, construction managers, and large specialty contractors who run multiple active jobs simultaneously and need an early-warning system for schedule slippage, budget variance, approval bottlenecks, and subcontractor performance - without waiting until the Friday meeting to find out something is off the rails.

## What it does

1. **Pulls all active job data each morning** - connects to Procore (schedule, RFIs, submittals, change orders, daily logs) and Sage 300 CRE or Viewpoint Vista (budget, cost at completion, committed costs)
2. **Flags jobs by risk category** - schedule risk, subcontractor milestone gaps, RFI/submittal delays, budget and change order exposure, procurement lead time threats, and inspection/permit issues
3. **Ranks flags by urgency** - Critical, High, and Watch tiers so the principal knows where to spend the first hour of the day
4. **Delivers the daily ops brief** - formatted summary with critical items first, one-line summaries for Watch-tier items, and a clean-project list confirming complete coverage
5. **Answers on-demand queries** - responds to specific questions like "What's our total pending change order exposure?" or "Which subs are behind this week?" by pulling from connected systems
6. **Escalates persistent flags** - automatically elevates issues that have been flagged for 3+ consecutive days without a status change so nothing quietly lingers
7. **Generates the Friday trend summary** - end-of-week report showing which projects were flagged, how long flags stayed open, and which risk categories are recurring

## Key integrations

- **Procore** - source for project schedule, milestone tracking, RFI log, submittal log, change order status, daily logs, and subcontractor activity
- **Sage 300 CRE** - source for budget, cost at completion, committed costs, and change order financial exposure
- **Viewpoint Vista** - alternative accounting source for project financials, cost at completion, and committed cost data
- **Email or Slack** - delivery channel for the daily ops brief

## Getting started

1. **Import this workspace** into Gamut using the workspace-zip import flow.
2. **Run the `agent-onboarding` skill** - the agent will ask about your systems, project types, risk thresholds, and who receives the daily brief.
3. **Give it your first task** - a good first prompt: "Pull today's job status and give me the ops brief."

---

Relevant subsegments: GCON
