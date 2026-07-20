> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/job-project-status/aec-job-project-status)** — one-click deploy, no setup.

# AEC Job/Project Status Agent

A daily operations intelligence agent for architecture, engineering, and design firms. Every morning it checks your active projects against schedule, milestones, billing, and approval queues, then delivers a prioritized brief so principals and PMs know exactly what to act on before the day starts.

---

## What it does

1. **Flags schedule slips** - compares planned vs. actual percent complete across all active jobs and surfaces any project falling behind by more than your configured threshold.
2. **Tracks milestone and deliverable gaps** - identifies deliverables past due or due within 7 days with no progress, and distinguishes internal delays from client/consultant holds.
3. **Surfaces approval and review bottlenecks** - monitors open RFIs, pending submittals, and unsubmitted invoices, and reports who is responsible for the next action and how long the item has been stalled.
4. **Identifies overbilling and unbilled backlog** - calculates earned value vs. billed for each project and flags overbilling risk, aging unbilled work, and projects approaching their not-to-exceed fee.
5. **Delivers a structured daily ops brief** - compiles all findings into a prioritized action list with project-level detail, delivered by email, Slack, or direct output at a scheduled time each morning.
6. **Answers on-demand project queries** - responds to specific questions about burn, budget, open RFIs, or unbilled amounts for any project, citing source system and data freshness.
7. **Escalates persistent issues** - automatically elevates items that have been flagged for multiple consecutive days without resolution, so nothing falls through the cracks.
8. **Reconciles data across systems** - when schedule data (Procore) and financial data (Deltek/BQE) come from different systems, it flags discrepancies and reports which system is the source of truth for each data type.

---

## Key integrations

- **Deltek Vision / Vantagepoint** - project financials, fee tracking, percent complete, invoice status, and subconsultant billing
- **BQE Core** - time and expense tracking, project budget vs. actual, invoice generation and approval workflow
- **Procore** - project schedule, milestones, RFI log, submittal log, and change order status

---

## Getting started

1. **Import this workspace** into Gamut by uploading the zip file and opening it as a new agent workspace.
2. **Run agent-onboarding** - type `/agent-onboarding` or ask the agent "let's set up the ops brief." The agent will walk you through connecting your systems, setting risk thresholds, and choosing how and when the brief is delivered.
3. **Trigger your first brief** - once setup is complete, ask the agent: "Run the daily ops brief." Review the output and adjust any thresholds that feel too noisy or too loose.

---

Relevant subsegments: AEC
