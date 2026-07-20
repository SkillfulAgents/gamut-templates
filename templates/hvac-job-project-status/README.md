> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/job-project-status/hvac-job-project-status)** — one-click deploy, no setup.

# HVAC/Plumbing/Electrical - Job / Project Status

Know which jobs are in trouble before 8am. This Gamut agent connects to ServiceTitan or FieldEdge, scans every open job each morning, and delivers a daily ops brief that surfaces jobs at risk — behind schedule, unscheduled, missing parts, stuck on permits, or stalled with no update — so the dispatcher or owner can intervene before a small problem becomes a callback or a missed SLA.

---

## Who this is for

Trade contractors who run multiple open jobs simultaneously and need a systematic way to catch problems before customers call — without the dispatcher having to manually dig through the platform every morning.

- HVAC contractors (service calls, installs, maintenance contracts)
- Plumbing contractors (residential and commercial)
- Electrical contractors (residential, commercial, industrial)
- Multi-trade contractors managing 10 to 100+ simultaneous open jobs in ServiceTitan or FieldEdge

**Relevant subsegments: HVAC**

---

## What it does

1. Pulls all open jobs from ServiceTitan or FieldEdge each morning and gives a total open-job count before diving into risk flags.
2. Classifies flagged jobs into five risk categories: behind schedule, unscheduled (no tech/appointment), missing parts or PO, awaiting permit or inspection, and stalled (no status update for 3+ days).
3. Ranks flagged jobs by urgency — commercial and service agreement customers with SLA obligations first, then residential by days overdue.
4. Delivers a concise daily ops brief formatted for quick review: job number, customer, risk type, and a specific recommended action per line.
5. Surfaces stalled job details — last status note, assigned tech, and days since last update — so the dispatcher knows exactly who to call.
6. Tracks recurring risk patterns and flags persistent problems (same job at risk 3+ consecutive days, technicians with chronic stalls, suppliers causing frequent delays).
7. Delivers a weekly summary: jobs completed, open jobs by risk category, average days-to-close, and pattern findings.

---

## Key integrations

- **ServiceTitan** — primary field service platform; pulls job records, technician assignments, appointment data, PO status, and permit flags
- **FieldEdge** — alternative field service platform; same job and status data pull
- Optional: parts supplier portal or PO system for more granular backorder tracking
- Optional: permit management tool for municipalities that support API lookups

---

## Getting started

1. **Import this workspace** into Gamut using the workspace import flow.
2. **Run the `agent-onboarding` skill** — it will walk you through connecting ServiceTitan or FieldEdge, setting stale-job thresholds, defining commercial vs. residential prioritization, and scheduling your daily brief.
3. **Give the agent its first task:** "Pull today's open jobs and show me anything flagged as at risk." Review the brief and ask it to expand on any flagged job for more detail.

---

## Configuration

**`CLAUDE.md` — `## Your context` section**
After onboarding, the agent fills in your business context here: trade type, platform connection, job volume, stall threshold (default 3 days), commercial account list, risk priority preferences, brief format, and delivery schedule.

Editable fields include:
- ServiceTitan or FieldEdge credentials / API connection
- Stall threshold in days (default: 3)
- Commercial and service-agreement account list
- Daily brief delivery time and channel
- Weekly summary day/time and channel
- Escalation contact for persistent-risk jobs
- Job types to exclude from flagging (e.g., long-lead installation projects with planned multi-week timelines)

---

## Pattern

Vertical skin — HVAC/Plumbing/Electrical flavor of the horizontal **Job / Project Status Tracker** template. Specialized for trade contractors using ServiceTitan or FieldEdge.
