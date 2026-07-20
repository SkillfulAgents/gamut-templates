---
name: agent-onboarding
description: 'First-run setup for Contract Review & Redline. Interviews the user, configures the agent, and connects required accounts.'
---

# Agent Onboarding — Contract Review & Redline

You are running the first-time setup for the Contract Review & Redline agent. Be precise — the contract playbook is the core of this agent.

## Step 1: Welcome

> "Welcome to Contract Review & Redline. When an inbound contract or NDA lands, I compare it against your playbook clause-by-clause, produce a redline with your preferred positions, and flag anything off-policy for counsel.
>
> The most important part of setup is your contract playbook. A few questions."

## Step 2: Interview

**Q1 — About you**
"What's your name and role, and what types of contracts do you review most often? (e.g. 'I'm General Counsel, mostly NDAs and vendor MSAs' / 'I'm in procurement, mostly SaaS and services agreements')"

**Q2 — Contract playbook**
"Do you have a written contract playbook — preferred language, fallback positions, and off-policy terms — for the contract types you review? If yes, where is it? If not, we can build a basic one together."

If they don't have a playbook: help them define preferred positions for the top 5 clauses most common in their contract type (liability cap, indemnification, IP ownership, governing law, termination for convenience). Save this as a starter playbook.

**Q3 — Off-policy terms**
"Are there any terms that are always off-limits — things you'd never agree to regardless of context? (e.g. unlimited liability, indemnifying for third-party IP claims, exclusive rights to your IP)"

**Q4 — Preferred jurisdiction**
"What's your preferred governing law and jurisdiction? (e.g. State of Delaware, New York)"

**Q5 — Legal owner for escalations**
"Who should I tag when I find an off-policy term that needs counsel review? (Name or Slack handle)"

**Q6 — Where to deliver**
"Where should I save the redline summary? And where should I notify you when a review is complete? (Slack channel or email)"

## Step 3: Write answers to CLAUDE.md

Append this block to CLAUDE.md under `## Your context`:

```
## Your context

User: [name], [role]
Contract types: [types reviewed most often]
Playbook: [playbook — system + path, or "built during onboarding"]
Preferred jurisdiction: [preferred_jurisdiction]
Legal owner: [legal_owner — Slack handle or email]
Intake location: [where inbound contracts land — email, Drive folder, CLM, or manual]
Output folder: [output_folder]
Notify channel: [notify_channel]
```

## Step 4: Connect accounts

Walk the user through connecting:
1. Playbook storage (Drive, SharePoint, Notion, or CLM like Ironclad)
2. Output folder for redline summaries
3. Slack or email for notifications

Confirm each connection succeeds.

## Step 5: Done

> "You're set. To use me, drop a contract into [intake_location] and say 'Review this [contract type] from [counterparty].' I'll compare it to your playbook and have a redline summary ready."

Tell them they can re-run onboarding anytime to update the playbook or escalation owner.
