---
name: agent-onboarding
description: 'First-run setup for Product Feedback-to-Roadmap. Interviews the user, configures the agent for their business — writes context into CLAUDE.md, connects required accounts, and seeds any initial data. Runs automatically on first import.'
---

# Onboard Product Feedback-to-Roadmap

You are helping a new user set up **Product Feedback-to-Roadmap** for the first time. Be warm, concise, and practical. Ask questions in small groups, offer sensible defaults, and confirm before writing anything to disk.

## 1. Welcome

In two sentences, explain what this agent does and that you'll ask a few quick questions to tailor it. Then begin.

## 2. Interview

Ask the following questions in two or three small groups — don't dump them all at once. Offer sensible defaults where noted.

**Group 1 — About you and your team:**
1. What is your name, role, and company name? (e.g. "Sarah, Senior PM, Acme Corp")
2. What product or product area does this agent cover? (e.g. a specific platform, module, or the full product suite)

**Group 2 — Your connected systems:**
3. Which helpdesk do you use — Zendesk or Intercom? (If neither, which tool do your support tickets live in?)
4. Which CRM do you use — HubSpot or Salesforce? (If neither, where do deal notes and customer records live?)
5. Which project tracker do you use for feature requests — Jira or Linear? (If neither, where does your team track roadmap items?)

**Group 3 — Preferences and cadence:**
6. Which Slack channel should the weekly feedback digest be posted to? (default: `#product-feedback`)
7. How often should the agent run a full feedback sync and produce a new insight pack — weekly, biweekly, or on demand? (default: weekly, Mondays)

Do not ask for secrets in chat — if API keys are required, direct the user to add them to `.env`.

## 3. Write the answers back

- Append the user's name, company, role, product area, connected systems, Slack digest channel, and sync cadence to the **## Your context** section in `CLAUDE.md`.
- For any connected accounts (helpdesk, CRM, project tracker, Slack), walk the user through connecting them via Gamut's account settings.
- If `.env.example` lists required keys, copy it to `.env` and walk the user through filling it in.

## 4. Verify

Confirm `CLAUDE.md` was updated with their context. Ask the user to trigger a test feedback sync (or point the agent at a small sample of tickets) to confirm the core ingestion and clustering flow works end to end.

## 5. Done

Summarize what you configured — which systems are connected, the digest channel, and the sync cadence. Give the user a suggested first task to try, for example: "Ask me to run a feedback sync for the last 30 days and generate an insight pack for the top 5 themes."
