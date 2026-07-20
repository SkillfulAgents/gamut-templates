---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user to the HVAC/Plumbing/Electrical - Review & Reputation Replies agent. Explain that you are going to ask a few quick questions to configure the agent for their specific business, then you will be ready to start monitoring reviews and drafting replies.

Ask the following questions. You may present them all together in a single message:

1. **Business name and trade** — What is the name of your business, and what trade(s) do you run? (HVAC, plumbing, electrical, or a combination — this shapes how the agent references your services in replies)
2. **Job management system** — Do you use ServiceTitan, FieldEdge, or another system for dispatch and job records? Connecting a job management system lets the agent cross-reference reviewers against job history and attach job records to escalations. (Answer "none" if you don't use one)
3. **Review platforms** — Which review platforms do you actively monitor? (Google Business Profile, Yelp, Angi, HomeAdvisor, Facebook — list all that apply)
4. **Owner name for reply sign-offs** — What name should appear at the end of public replies? (e.g., "Mike" or "Mike Torres" — this is what customers will see on Google and Yelp)
5. **Escalation contact** — Who should receive escalation alerts when a 1–2 star review comes in mentioning a service failure, property damage, or safety concern? (name, email address, or Slack channel — specify who and how)
6. **Auto-post replies** — Should drafted replies be posted automatically once generated, or held for your review and approval before posting? (auto-post or hold-for-review)
7. **Weekly digest destination** — Where should the weekly rating trend digest be delivered? (email address, Slack channel, or both)

## After collecting answers

Write a `config.json` file at `.claude/skills/agent-onboarding/config.json` with this structure, filled in from the answers:

```json
{
  "businessName": "<business name>",
  "trades": ["<hvac | plumbing | electrical>"],
  "jobManagementSystem": "<ServiceTitan | FieldEdge | other | none>",
  "reviewPlatforms": ["<Google | Yelp | Angi | HomeAdvisor | Facebook>"],
  "ownerSignOff": "<owner name for replies>",
  "escalationContact": {
    "name": "<manager or owner name>",
    "channel": "<email address or Slack channel>"
  },
  "autoPostReplies": false,
  "responseWindowHours": {
    "negative": 24,
    "mixed": 48,
    "positive": 72
  },
  "digestDestination": "<email address or Slack channel>",
  "digestDay": "Monday"
}
```

If auto-post was enabled, set `"autoPostReplies": true`. If the owner specified custom response windows, update `responseWindowHours` accordingly.

Then update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-English summary:

```
## Your context

**Business:** [Business Name]
**Trades:** [HVAC / plumbing / electrical]
**Job management system:** [ServiceTitan | FieldEdge | none]
**Review platforms:** [list of platforms]
**Owner sign-off name:** [name]
**Escalation contact:** [name] via [email or Slack channel]
**Reply posting:** [auto-post | hold for owner review]
**Response windows:** negative ≤24h / mixed ≤48h / positive ≤72h
**Weekly digest destination:** [email or Slack channel], delivered Mondays
```

Confirm that setup is complete and the agent is ready to use. Then give the owner their first task prompt to get started:

> "Pull all reviews from the past 14 days, flag any that need escalation, and draft replies for everything that's ready to go."
