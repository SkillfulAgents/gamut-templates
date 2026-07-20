---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user to the Cleaning/Janitorial - Invoice & AR Chase agent. Explain that you are going to ask a few quick questions to configure the agent for their specific business, then you will be ready to start chasing invoices.

Ask the following questions. You may present them all together in a single message:

1. **Business name** — What is the name of your cleaning or janitorial company?
2. **Invoicing system** — Where do you track and manage invoices? (Swept, Janitorial Manager, QuickBooks, Xero, spreadsheet, or other — be specific so the agent knows where to pull invoice data from)
3. **Owner name for outreach** — What name should sign off on follow-up messages to clients? (e.g., "Maria" or "Maria Santos" — this is what clients will see)
4. **AR escalation thresholds** — Do you want to use the default aging tiers (1–14 days: first reminder, 15–30 days: second reminder, 31–60 days: firm notice, 60+ days: escalation notice), or would you like to adjust when each tier kicks in?
5. **Outreach channel** — Should client follow-ups go by email, SMS/text, or both? If SMS, confirm clients have opted in.
6. **Digest and alert destination** — Where should the weekly AR digest and escalation alerts be sent? (email address, Slack channel, or both)

## After collecting answers

Write a `config.json` file at `.claude/skills/agent-onboarding/config.json` with this structure, filled in from the answers:

```json
{
  "businessName": "<business name>",
  "invoicingSystem": "<system name>",
  "ownerName": "<owner name for sign-offs>",
  "arThresholds": {
    "firstReminder": 14,
    "secondReminder": 30,
    "firmNotice": 60,
    "escalation": 61
  },
  "outreachChannel": "<email | sms | both>",
  "digestDestination": "<email address or Slack channel>",
  "autoEscalation": false
}
```

If the owner customized the aging thresholds, update the values in `arThresholds` accordingly.

Then update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-English summary:

```
## Your context

**Business:** [Business Name]
**Invoicing system:** [system]
**Owner name for outreach sign-offs:** [name]
**AR aging tiers:** first reminder ≤14d / second reminder 15–30d / firm notice 31–60d / escalation 60+d
**Client outreach channel:** [email | SMS | both]
**Digest & alert destination:** [email or Slack channel]
**Auto-escalation:** disabled (owner approval required before escalation notices)
```

Confirm that setup is complete and the agent is ready to use. Then give the owner their first task prompt to get started:

> "Show me all invoices over 30 days past due and draft a follow-up for each one."
