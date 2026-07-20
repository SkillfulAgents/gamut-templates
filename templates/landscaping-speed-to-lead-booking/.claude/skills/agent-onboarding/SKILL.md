---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user to the Landscaping/Lawn - Speed-to-Lead & Booking agent. Explain that you are going to ask a few quick questions to configure the agent for their specific business and lead flow, then the agent will be ready to start responding to inbound leads and booking estimates.

Ask the following questions. You may present them all together in a single message:

1. **Business name** — What is the name of your landscaping or lawn care company?
2. **Scheduling system** — Do you manage your schedule and client records in Jobber, Aspire, or another system? (Be specific — the agent needs to know where to create job records and check availability.)
3. **Lead sources** — Which channels do inbound leads come from? (Check all that apply: website/web form, Thumbtack, Angi, HomeAdvisor, phone/voicemail, SMS/text, referral form, or other — list any others.)
4. **Preferred reply channel** — When a new lead comes in, should the agent reply by SMS, email, or match the channel the lead came from? And what phone number or email address should outreach come from?
5. **Services you offer** — What are your main service types? (e.g., weekly lawn mowing, fertilization programs, landscape installs, irrigation, seasonal cleanups, commercial contracts) — this shapes the qualification questions the agent asks each lead.
6. **Owner or office name for sign-offs** — What name should sign outbound messages to prospects? (e.g., "Jake" or "Jake at Green Edge Lawn")
7. **Digest destination** — Where should the daily lead digest and unworked-lead alerts be sent? (email address, SMS number, or Slack channel)

## After collecting answers

Write a `config.json` file at `.claude/skills/agent-onboarding/config.json` with this structure, filled in from the answers:

```json
{
  "businessName": "<business name>",
  "schedulingSystem": "<Jobber | Aspire | other>",
  "leadSources": ["<source1>", "<source2>"],
  "replyChannel": "<sms | email | match-source>",
  "outreachFrom": "<phone number or email address>",
  "serviceTypes": ["<service1>", "<service2>"],
  "ownerName": "<name for sign-offs>",
  "followUpIntervalHours": 4,
  "staleLeadThresholdHours": 72,
  "maxFollowUps": 2,
  "digestDestination": "<email, SMS number, or Slack channel>"
}
```

Then update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-English summary:

```
## Your context

**Business:** [Business Name]
**Scheduling system:** [Jobber | Aspire | other]
**Lead sources:** [list]
**Reply channel:** [sms | email | match-source] from [outreach number/address]
**Services offered:** [list]
**Owner name for outreach sign-offs:** [name]
**Follow-up interval:** every 4 hours during business hours
**Stale lead threshold:** 72 hours with no response
**Max unsolicited follow-ups per lead:** 2
**Digest & alert destination:** [email, SMS, or Slack channel]
```

Confirm that setup is complete and the agent is ready to use. Then give the owner their first task prompt to get started:

> "Show me all leads from the past 48 hours and tell me which ones are unworked."
