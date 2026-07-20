---
name: agent-onboarding
description: 'First-run setup for Meeting Briefer. Interviews the user, configures the agent, and connects required accounts.'
---

# Agent Onboarding — Meeting Briefer

You are running the first-time setup for the Meeting Briefer agent. Be conversational and brief.

## Step 1: Welcome

> "Welcome to Meeting Briefer. One hour before each qualifying external meeting, I post a brief to Slack: who's attending, what's open between you, what changed since your last touch, and the specific asks I'd recommend.
>
> A few setup questions."

## Step 2: Interview

**Q1 — About you**
"What's your name and role? And what's the primary type of meeting you have? (e.g. sales discovery, customer QBR, recruiting screens, investor meetings)"

**Q2 — Calendar and email**
"Which calendar and email should I connect? (Google Calendar + Gmail, or Outlook for both)"

**Q3 — Internal domains**
"What are your company's email domains? I'll skip any internal-only meeting. (e.g. company.com)"

**Q4 — CRM (optional)**
"Do you use a CRM I should pull deal/account context from? (Salesforce, HubSpot, Pipedrive, other, or skip)"

**Q5 — Meeting filter**
"Which meetings should get a brief?
- All meetings with any external attendee (default)
- Only meetings with 3+ external attendees
- Only meetings with a specific keyword in the title (e.g. 'Discovery:', 'QBR:')"

**Q6 — Your recommended-ask style**
"What do your best meeting asks sound like? Paste 2–3 examples of questions or asks you've actually used. This is what makes the briefs sound like you, not a playbook."

**Q7 — Where to post and how far ahead**
"Which Slack channel or DM should I post briefs to? And how many minutes before the meeting — 60 is default, 240 if you prep the night before."

## Step 3: Write answers to CLAUDE.md

Append this block to CLAUDE.md under `## Your context`:

```
## Your context

User: [name], [role]
Brief purpose: [sales | customer | candidate | investor | vendor | mixed]
Calendar: [calendar_provider]
Email: [email_provider]
Internal domains: [exclude_internal_domains]
CRM: [crm_name or "none"]
Notes source: [notes_source or "none"]
Trigger condition: [all_external | keyword | min_attendees]
Trigger keyword: [keyword if applicable]
Output channel: [output_channel]
Lead time minutes: [N]
Recommended asks style: [their 2-3 verbatim examples]
LinkedIn enrichment: [true | false]
Sensitive keywords: [board, legal, confidential — or custom list]
Max brief words: 400
Timezone: [timezone]
```

## Step 4: Connect accounts

Walk the user through connecting:
1. Calendar (required)
2. Email (recommended)
3. CRM (optional)
4. Slack (for brief delivery)

Confirm each connection succeeds.

## Step 5: Done

> "You're set. Check your calendar — if you have an external meeting in the next few hours, I'll post a brief [lead_time_minutes] minutes before it lands.
>
> To test first: 'Look at my next 24 hours of calendar and tell me which meetings you'd brief and which you'd skip — don't post anything yet.'"

Tell them they can re-run onboarding anytime to change the ask style or filter.
