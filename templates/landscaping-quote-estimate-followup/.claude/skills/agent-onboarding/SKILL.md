---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user to the Landscaping/Lawn - Quote / Estimate Follow-up agent. Explain that you are going to ask a few quick questions to configure the agent for their specific business and quoting process, then the agent will be ready to start tracking open estimates and following up with prospects.

Ask the following questions. You may present them all together in a single message:

1. **Business name** — What is the name of your landscaping or lawn care company?
2. **Quoting system** — Do you manage quotes and estimates in Jobber, Aspire, or another system? (Be specific — if Jobber, confirm whether you use the Quotes module; if Aspire, confirm you have the Sales module active; if another system or spreadsheet, describe how quotes are tracked)
3. **Owner name for outreach** — What name should sign off on follow-up messages to prospects? (e.g., "Mike" or "Mike Castellano" — this is what prospects will see)
4. **Service types you quote** — What are your main service categories? (e.g., weekly lawn maintenance, one-time cleanups, irrigation install, hardscape/patio, landscape design/build, snow removal) — this lets the agent break out win-rate by service type in reports
5. **Follow-up timing** — Do you want to use the default follow-up windows (first follow-up at 5 days, second at 10 days, final nudge at 15+ days, expiration warning 3 days before expiry), or would you like to adjust any of these?
6. **Quote dollar threshold for owner review** — Above what quote value should the agent flag a follow-up for your review before sending, rather than auto-sending? (e.g., quotes over $5,000 get reviewed first)
7. **Report & alert destination** — Where should the weekly pipeline report and daily expiration alerts be delivered? (email address, Slack channel, or both)

## After collecting answers

Write a `config.json` file at `.claude/skills/agent-onboarding/config.json` with this structure, filled in from the answers:

```json
{
  "businessName": "<business name>",
  "quotingSystem": "<Jobber | Aspire | other>",
  "ownerName": "<owner name for sign-offs>",
  "serviceTypes": ["<service type 1>", "<service type 2>"],
  "followUpWindows": {
    "firstFollowUpDays": 5,
    "secondFollowUpDays": 10,
    "finalNudgeDays": 15,
    "expirationWarningDays": 3
  },
  "ownerReviewThreshold": 5000,
  "outreachChannel": "<email | sms | both>",
  "reportDestination": "<email address or Slack channel>",
  "autoSendFinalNudge": false
}
```

If the owner customized the follow-up timing windows or threshold, update the values accordingly.

Then update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-English summary:

```
## Your context

**Business:** [Business Name]
**Quoting system:** [Jobber | Aspire | other]
**Owner name for outreach sign-offs:** [name]
**Service types:** [list]
**Follow-up windows:** first ≤5d / second ≤10d / final nudge 15+d / expiration warning 3d before expiry
**Owner review threshold:** quotes over $[amount] require approval before final nudge or expiration warning is sent
**Outreach channel:** [email | SMS | both]
**Report & alert destination:** [email or Slack channel]
**Auto-send final nudge:** disabled (owner approval required)
```

Confirm that setup is complete and the agent is ready to use. Then give the owner their first task prompt to get started:

> "Show me all quotes that have been open for more than 7 days with no response and draft a follow-up for each one."
