---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user warmly and explain that this short setup will configure the Review & Reputation Replies agent for their specific dealership. Tell them it takes about 5 minutes and covers their platforms, voice, and escalation contacts — after which the agent is ready to start monitoring and drafting replies.

Work through the following questions conversationally. Ask one or two at a time, not all at once. Acknowledge each answer before moving to the next.

---

## Onboarding Questions

**Question 1 — Dealership basics**

Ask:
- What is the full name of your dealership or service center? (e.g., "Westside Toyota" or "Riverside Auto Group")
- What city and state are you located in?
- Is this a single-point dealership or a multi-location group? If multi-location, how many rooftops should this agent cover, and should replies be branded per location or under one group name?

**Question 2 — Review platforms**

Ask:
- Which review platforms do you currently have active profiles on? (Google Business Profile, DealerRater, Yelp — or others?)
- Do you have API access or partner credentials set up for any of these platforms, or will you be connecting them through a third-party reputation management tool (e.g., Podium, Birdeye, Reputation.com)?
- How often would you like the agent to check for new reviews? (Default is every 4 hours during business hours — Mon–Sat 8 AM to 6 PM local time.)

**Question 3 — Departments and escalation contacts**

Ask:
- Which departments should this agent cover? (Sales, Service, Parts, F&I, or all of the above?)
- Who should receive immediate alerts for 1–2 star reviews? Please provide: name, title, and preferred contact method (email address, Slack channel, or phone number for SMS).
- Who should receive the weekly Monday morning digest? (List names and emails — can be the same person or a broader group like the GM and service manager.)

**Question 4 — Brand voice and tone**

Ask:
- How would you describe your dealership's communication style? Choose the closest match or describe your own:
  - Warm and casual (friendly, first-name basis, conversational)
  - Professional and polished (formal, brand-forward, minimal personality)
  - Family-oriented (community-focused, personal touch, longstanding relationships)
- Are there any phrases, words, or topics you want the agent to always avoid in replies? (e.g., competitor names, specific pricing language, legal disclaimers)
- Is there a specific sign-off or closing line you use in customer communications? (e.g., "See you on the lot!" or "Thank you for your business.")

**Question 5 — DMS and CRM integration**

Ask:
- Are you currently using CDK Global, Reynolds & Reynolds, or VinSolutions? If so, which one(s)?
- Do you want the agent to attempt to match reviews to repair orders or customer records in your DMS/CRM for context when drafting replies? (This requires API credentials — you can skip for now and add later.)
- For 1–2 star reviews, should the agent automatically create a follow-up task in VinSolutions (or your CRM) assigned to the service manager, or just send the alert notification?

**Question 6 — Approval workflow**

Ask:
- Who should approve reply drafts before they are posted? (e.g., service advisor approves service reviews, sales manager approves sales reviews, or a single marketing contact approves all)
- How would you like drafts delivered for approval? Options:
  - Email digest of pending drafts (daily or as they come in)
  - Slack message with approve/edit/reject options
  - Direct in the Gamut chat interface
- What is your target reply turnaround time? (e.g., same business day, within 4 hours, within 24 hours) — this will be tracked in the weekly digest.

---

## After Collecting Answers

Once you have all the answers, do the following:

### 1. Write the `## Your context` section in CLAUDE.md

Replace the `<!-- Filled in during onboarding -->` placeholder in `/workspace/CLAUDE.md` (or the active workspace's CLAUDE.md) with a filled-in context block like this — substituting the user's actual answers:

```
## Your context

**Dealership:** [Full dealership name], [City, State]
**Structure:** [Single-point / Multi-location — N rooftops, branded as: ...]

**Active review platforms:** [Google Business Profile, DealerRater, Yelp, ...]
**Platform connection method:** [Direct API credentials / Third-party tool: ...]
**Monitoring cadence:** Every [N] hours, [days and hours]

**Departments covered:** [Sales / Service / Parts / F&I / All]

**Escalation contacts (1–2 star reviews):**
- [Name], [Title] — [email / Slack / SMS]

**Weekly digest recipients:**
- [Name, email]
- [Name, email]

**Brand voice:** [Warm and casual / Professional and polished / Family-oriented / Custom description]
**Avoid in replies:** [List any restricted phrases or topics]
**Standard sign-off:** "[Sign-off line]"

**DMS/CRM:** [CDK Global / Reynolds & Reynolds / VinSolutions / None connected]
**DMS review matching:** [Enabled / Disabled / To be configured]
**Auto-create follow-up tasks in CRM:** [Yes / No]

**Reply approval workflow:**
- Approver(s): [Name(s) and role(s)]
- Delivery method: [Email digest / Slack / Gamut chat]
- Target turnaround: [Same day / 4 hours / 24 hours]
```

### 2. Write config.json

Create or update `.claude/config.json` in the workspace with the structured configuration:

```json
{
  "dealership": {
    "name": "<dealership name>",
    "location": "<city, state>",
    "structure": "<single-point or multi-location>",
    "locations": []
  },
  "platforms": {
    "google": { "enabled": true, "connectionMethod": "<api-direct or third-party tool name>" },
    "dealerRater": { "enabled": true, "connectionMethod": "<api-direct or third-party tool name>" },
    "yelp": { "enabled": true, "connectionMethod": "<api-direct or third-party tool name>" }
  },
  "monitoring": {
    "cadence": "<e.g. every-4-hours>",
    "activeDays": ["monday","tuesday","wednesday","thursday","friday","saturday"],
    "activeHoursStart": "08:00",
    "activeHoursEnd": "18:00",
    "timezone": "<e.g. America/Los_Angeles>"
  },
  "departments": ["sales","service","parts","fi"],
  "escalation": {
    "lowStarThreshold": 2,
    "contacts": [
      { "name": "", "title": "", "method": "email", "address": "" }
    ]
  },
  "digest": {
    "frequency": "weekly",
    "dayOfWeek": "monday",
    "sendTime": "08:00",
    "recipients": []
  },
  "voice": {
    "style": "<warm-casual | professional-polished | family-oriented | custom>",
    "avoidPhrases": [],
    "signOff": ""
  },
  "dms": {
    "system": "<cdk | reynolds | vinsolutions | none>",
    "reviewMatching": false,
    "autoCreateFollowUpTasks": false
  },
  "approvalWorkflow": {
    "approvers": [],
    "deliveryMethod": "<email-digest | slack | gamut-chat>",
    "targetTurnaroundHours": 24
  }
}
```

### 3. Confirm and hand off

Tell the user their configuration is saved and the agent is ready to use. Then give them their first task prompt to try:

> "Check for any new reviews posted in the last 24 hours across Google, DealerRater, and Yelp. Draft replies for anything 3 stars and above, and flag any 1–2 star reviews for [manager name]'s immediate attention."

Remind them they can edit `.claude/config.json` or the `## Your context` section of `CLAUDE.md` at any time to update settings, and they can re-run `/agent-onboarding` to go through setup again.
