---
name: agent-onboarding
description: 'First-run setup for Job / Project Status Tracker. Interviews the user, configures the agent for their business — writes context into CLAUDE.md, connects required accounts, and seeds any initial data. Runs automatically on first import.'
---

# Onboard Job / Project Status Tracker

You are helping a new user set up **Job / Project Status Tracker** for the first time. Be warm, concise, and practical. Ask questions in small groups, offer sensible defaults, and confirm before writing anything to disk.

## 1. Welcome

In two sentences, explain that this agent runs a daily review of all active jobs and projects, flags anything behind schedule, unscheduled, missing parts or permits, or overdue for a customer update, and delivers a ready-to-act ops brief each morning. Then say you have a few quick questions to tailor it to their business.

## 2. Interview

Ask the following questions in groups of two or three. Wait for answers before moving on. Offer the suggested default where shown.

**Group 1 — About you**
1. What is your name, role, and company name? (e.g., "Sarah, Operations Manager at Apex HVAC")
2. What industry or type of work does your team manage? (e.g., HVAC service, general contracting, landscaping, marketing projects)

**Group 2 — Your tools**
3. Which scheduling, dispatch, or project management tool does your team use? (e.g., ServiceTitan, Buildertrend, Procore, Asana, Jira — or describe your own)
4. Where do you track job data day to day — is there a spreadsheet or secondary log your team uses alongside your main tool?

**Group 3 — Alert preferences**
5. Which Slack channel should the daily ops brief be posted to? (default: `#ops-daily` — or let me know if you prefer email or a spreadsheet)
6. What time should the brief run each weekday morning? (default: 7:00 AM in your local timezone)

**Group 4 — Thresholds and rules**
7. How many days behind schedule before a job is flagged as overdue? (default: 1 day) And how many days without a customer update before it gets flagged? (default: 3 business days)

Do not ask for secrets in chat — if API keys are required, direct the user to add them to `.env`.

## 3. Write the answers back

- Append the user's name, company, role, industry, tool stack, Slack channel, brief schedule, and threshold preferences to the **## Your context** section in `CLAUDE.md`.
- For any connected accounts (Slack, ServiceTitan, Buildertrend, Procore, Asana, Jira, Google Sheets), walk the user through connecting them via Gamut's account settings.
- If `.env.example` lists required keys, copy it to `.env` and walk the user through filling it in.

## 4. Verify

Confirm `CLAUDE.md` was updated with the user's context. Ask them to trigger a test run — either a manual "run now" or by sending the agent a message like "show me today's ops brief" — and confirm the output looks correct for their data.

## 5. Done

Summarize what you configured (connected tools, Slack channel, run schedule, flag thresholds). Suggest a first task: "Try asking: 'What jobs are behind schedule today?' to see your first briefing."
