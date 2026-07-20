---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user to the Landscaping/Lawn - Review & Reputation Replies agent. Explain that you are going to ask a few quick questions to configure the agent for their specific business and review workflow, then you will be ready to start monitoring reviews and drafting replies.

Ask the following questions. You may present them all together in a single message:

1. **Business name and owner/manager name** — What is the name of your landscaping or lawn care business, and what name should sign off on review replies? (e.g., "Mike" or "Mike Torres" — this is the name reviewers will see responding)
2. **Review platforms** — Which platforms do you receive reviews on? (Google Business Profile, Yelp, Facebook, HomeAdvisor, Angi, Thumbtack, or others — list all that apply so the agent knows where to monitor)
3. **Job management system** — Do you use Jobber, Aspire, both, or another system to track jobs and customer records? This lets the agent match reviews to specific jobs and pull crew and service details when drafting replies.
4. **Customer mix** — Is your business primarily residential, commercial (property managers, HOAs, businesses), or a mix? This shapes how the agent looks up job records and phrases replies — commercial accounts often need a more formal tone.
5. **Service failure escalation routing** — When a 1–2 star review comes in, who should be alerted before a reply is posted, and how? (email address, Slack channel, or SMS number — and how long should the agent wait for approval before sending a reminder?)
6. **Reply auto-approval for positive reviews** — Should the agent auto-post replies to 3–5 star reviews without approval, or do you want to review all replies before they go live? (Most operators auto-approve positives and require approval only for negative reviews)
7. **Weekly digest destination** — Where should the weekly rating trend digest be sent? (email address, Slack channel, or both — and which day of the week works best for you?)

## After collecting answers

Write a `config.json` file at `.claude/skills/agent-onboarding/config.json` with this structure, filled in from the answers:

```json
{
  "businessName": "<business name>",
  "ownerName": "<name for reply sign-offs>",
  "reviewPlatforms": ["<platform1>", "<platform2>"],
  "jobManagementSystem": "<Jobber | Aspire | both | other>",
  "customerMix": "<residential | commercial | mixed>",
  "escalationContact": "<email address, Slack channel, or SMS number>",
  "escalationSlaHours": 24,
  "autoApprovePositiveReplies": true,
  "digestDestination": "<email address or Slack channel>",
  "digestDay": "Monday"
}
```

If the operator set a custom escalation SLA window, update `escalationSlaHours` accordingly. If they want to review all replies before posting, set `autoApprovePositiveReplies` to `false`.

Then update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-English summary:

```
## Your context

**Business:** [Business Name]
**Owner name for reply sign-offs:** [name]
**Review platforms monitored:** [list]
**Job management system:** [Jobber | Aspire | both | other]
**Customer mix:** [residential | commercial | mixed]
**Service failure escalation:** [contact method] — [X]-hour SLA for manager approval before reply is posted
**Auto-approve positive reviews (3–5 star):** [yes | no — all replies require approval]
**Weekly digest destination:** [email or Slack channel], delivered [day]
```

Confirm that setup is complete and the agent is ready to use. Then give the owner their first task prompt to get started:

> "Pull all reviews from the past 30 days, triage them by urgency, and draft replies for any that haven't been answered yet."
