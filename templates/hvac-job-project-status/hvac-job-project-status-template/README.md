# HVAC / Plumbing / Electrical — Job / Project Status

Thirty open jobs on a dispatch board is not a problem — until the one that needs a permit inspection quietly ages into a contract dispute. This agent pulls your live job board from ServiceTitan or FieldEdge every morning, flags every job that is behind, stalled, unscheduled, or missing parts, and lands a plain-language ops brief in your inbox before the day starts.

## Who this is for

Field service contractors — HVAC, plumbing, electrical, or multi-trade — running 10 to 100+ jobs per week who need a morning visibility layer without building custom reports or hiring an ops analyst. Works with any shop that uses ServiceTitan or FieldEdge as their system of record.

**Relevant subsegments: HVAC**

Typical users: dispatcher, service manager, or owner-operator who is the first one in the office and needs to know where to focus in the first 30 minutes.

## What it does

1. **Pulls the open job board** from ServiceTitan or FieldEdge each morning at your configured time.
2. **Flags jobs at risk** across five categories: behind schedule (past estimated completion date), unscheduled (no tech or no appointment), missing parts (backorder or PO not received), awaiting permit inspection (inspection not scheduled), and stalled (no status update in 3+ days).
3. **Ranks flagged jobs by urgency** — commercial contracts and service agreements first, then residential, each sorted by days overdue.
4. **Delivers a concise daily ops brief** — bulleted list with job number, customer name, risk type, and a one-sentence recommended action for each flagged job.
5. **Surfaces stalled-job context** — for every stalled job, shows the last recorded status note and the assigned tech's name so you can follow up in one call.
6. **Detects recurring patterns** — if the same failure type (e.g., missed part orders) shows up three or more times in a week, it flags the systemic issue before it becomes a habit.
7. **Sends a weekly summary** — jobs completed, open jobs by risk category, and average days-to-close this week vs. last week.

## Key integrations

- **ServiceTitan** — open job list, job details, technician assignments, part/PO status, permit status
- **FieldEdge** — same data points via API or export
- **Email or Slack** — brief and summary delivery to dispatcher, owner, or both

## Getting started

1. **Import this workspace** into Gamut using the workspace zip.
2. **Run the `agent-onboarding` skill** — the agent will ask a short set of questions about your business, your platform, your risk thresholds, and where to send the brief.
3. **Send your first prompt** — try: *"Pull today's job board and give me the ops brief."*

## Configuration

All configuration is captured during onboarding and stored in `CLAUDE.md`. You can update it at any time by editing that file or re-running the onboarding skill. Key settings include:

| Setting | Default |
|---|---|
| Field service platform | ServiceTitan |
| Daily brief time | 7:00 AM local |
| Behind-schedule threshold | 1 day past estimated completion |
| Stalled threshold | 3 days without status update |
| Brief recipients | Dispatcher |
| Weekly summary day | Monday |
| Priority: commercial over residential | Yes |

## Pattern

Vertical — NON-TECH / HVAC, plumbing & electrical field operations
