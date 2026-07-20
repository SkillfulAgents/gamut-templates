---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user to the HVAC/Plumbing/Electrical - Quote / Estimate Follow-up agent. Explain that you are going to ask a few quick questions to configure the agent for their specific contracting business and estimating workflow, then you will be ready to start tracking open quotes and following up with prospects.

Ask the following questions. You may present them all together in a single message:

1. **Business name and trade type** — What is the name of your company, and what trade(s) do you primarily work in? (HVAC, plumbing, electrical, or a mix — this helps tailor follow-up message language to the right job types)
2. **Field service management system** — Where do you track estimates and jobs? (ServiceTitan, FieldEdge, spreadsheet, or other — be specific so the agent knows where to pull open estimate data from)
3. **Estimator name for outreach** — What name should sign off on follow-up messages to prospects? (e.g., "Mike" or "Mike Torres" — this is what prospects will see)
4. **Follow-up timing windows** — Do you want to use the default windows (first nudge at 3–5 days for service calls, 7 days for installs; second check-in at day 6–10; expiration warning 5 days before expiry), or would you like to adjust when each step triggers?
5. **Estimate expiration policy** — Do your estimates have a standard expiration period? (e.g., 30 days, 60 days, or no set expiry) This controls when the agent flags estimates as expiring and sends expiration notices.
6. **Outreach channel** — Should prospect follow-ups go by email, SMS/text, or both? If SMS, confirm prospects have opted in or provided a mobile number.
7. **Report destination and cadence** — Where should the weekly win-rate and pipeline report be delivered, and on which day? (email address, Slack channel, or both; default is Monday morning)

## After collecting answers

Write a `config.json` file at `.claude/skills/agent-onboarding/config.json` with this structure, filled in from the answers:

```json
{
  "businessName": "<business name>",
  "tradeType": "<hvac | plumbing | electrical | mixed>",
  "fsmSystem": "<ServiceTitan | FieldEdge | other>",
  "estimatorName": "<name for sign-offs>",
  "followUpWindows": {
    "serviceCalls": {
      "firstNudgeDays": 3,
      "secondCheckinDays": 7
    },
    "installs": {
      "firstNudgeDays": 7,
      "secondCheckinDays": 12
    },
    "expirationWarningDays": 5
  },
  "estimateExpirationDays": 30,
  "outreachChannel": "<email | sms | both>",
  "reportDestination": "<email address or Slack channel>",
  "reportDay": "monday",
  "autoSendExpirationNotices": false
}
```

If the owner customized follow-up timing or expiration policy, update the values accordingly.

Then update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-English summary:

```
## Your context

**Business:** [Business Name]
**Trade type:** [HVAC | plumbing | electrical | mixed]
**FSM system:** [ServiceTitan | FieldEdge | other]
**Estimator name for sign-offs:** [name]
**Follow-up windows:** service calls — first nudge day [X], second check-in day [X]; installs — first nudge day [X], second check-in day [X]
**Expiration warning:** [X] days before estimate expires
**Standard estimate expiration:** [X] days
**Prospect outreach channel:** [email | SMS | both]
**Report destination:** [email or Slack channel], delivered [day]
**Auto-send expiration notices:** disabled (owner approval required)
```

Confirm that setup is complete and the agent is ready to use. Then give the owner their first task prompt to get started:

> "Show me all open estimates older than 5 days and draft a follow-up message for each one."
