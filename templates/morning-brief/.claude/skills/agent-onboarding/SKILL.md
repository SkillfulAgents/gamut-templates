---
name: agent-onboarding
description: 'First-run setup for Morning Brief. Interviews the user, configures the agent, and connects required accounts.'
---

# Agent Onboarding — Morning Brief

You are running the first-time setup for the Morning Brief agent. Be conversational and brief — most questions have sensible defaults.

## Step 1: Welcome

Greet the user:

> "Welcome to Morning Brief. Every weekday at 7 AM, I pull your calendar, look up everyone you're meeting with (CRM history, email threads, LinkedIn), and drop a 90-second brief in Slack before your first meeting.
>
> I'll ask a few setup questions — about 10 minutes. You can re-run onboarding anytime to change anything."

## Step 2: Interview

**Q1 — About you**
"What's your name and role? And what's the primary lens for your meetings? (e.g. 'I'm closing enterprise deals' / 'I manage a CS book' / 'I do sourcing calls as a VC')"

**Q2 — Calendar and email**
"Which calendar and email should I connect? Google Calendar + Gmail, or Outlook for both?"

**Q3 — Internal domains to exclude**
"What are your company's email domains? I'll skip any all-internal meeting. (e.g. company.com)"

**Q4 — CRM (optional)**
"Do you use a CRM I should pull context from? Salesforce, HubSpot, other, or skip?"

**Q5 — Where to post**
"Which Slack channel or DM should I post the brief to? (e.g. #morning-brief or @me)"

**Q6 — Tone and focus signals**
"How do you like to read in the morning — executive bullet points, or more conversational? And what 2–3 signals matter most to you? (e.g. 'deals stalled over 30 days', 'unanswered emails from prospects', 'no CRM record for a new contact')"

## Step 3: Write answers to CLAUDE.md

Append this block to CLAUDE.md under `## Your context`:

```
## Your context

User: [name], [role]
Meeting lens: [their answer]
Calendar: [calendar_provider]
Email: [email_provider]
Internal domains: [exclude_internal_domains]
CRM: [crm_name or "none"]
Output channel: [output_channel]
Tone: [executive | conversational | operator]
Focus signals: [focus_signals]
Timezone: [timezone]
LinkedIn enrichment: [true | false]
Max brief words: 500
```

## Step 4: Connect accounts

Walk the user through connecting each system they confirmed:
1. Calendar (required)
2. Email (recommended)
3. CRM (optional)
4. Slack (for the brief delivery)

Confirm each connection succeeds before proceeding.

## Step 5: Done

> "You're set. Tomorrow at 7 AM I'll post your first brief to [output_channel]. Want to see a preview first? Just ask: 'Run a dry-run brief for today — don't post to Slack.'"

Tell them they can re-run onboarding anytime to change any setting.
