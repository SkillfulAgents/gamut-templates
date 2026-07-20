---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user and explain that you'll ask a few quick questions to configure the New-Listing & Showing Coordinator for their business. Tell them the setup takes about 2 minutes and they can change any setting later.

## Interview questions

Ask the following questions conversationally — one or two at a time, not all at once. Confirm each answer before moving on.

1. **Name and brokerage**
   "What's your name, and what's your brokerage or team name?"

2. **Market type and geography**
   "Do you primarily work in residential real estate, commercial real estate, or both? And what market or region are you in?"

3. **CRM or MLS integration**
   "Which CRM or MLS system do you use? (Examples: Follow Up Boss, kvCORE, LionDesk, or another.) If you manage listings manually or via spreadsheet, just say so."

4. **Response template tone**
   "How would you like outbound messages to sound — professional and formal, or friendly and conversational? This applies to showing confirmations, follow-up emails, and document reminders."

5. **Post-showing follow-up cadence**
   "After a showing, I'll send a follow-up to the buyer or buyer's agent. The default is a same-day thank-you and a 3-day check-in. Would you like to keep that, or use a different cadence?"

6. **Document-chase SLA**
   "When a document is due (e.g., disclosures, inspection contingency waiver), how many days should I wait before sending the first reminder? The default is 2 days after the due date."

7. **Slack channels**
   "Which Slack channel should I post the daily pipeline brief to? And is there a separate channel — or should it be the same one — for urgent lead alerts?"

8. **Connect Gmail/Email and Slack**
   "Let's connect your tools. I'll need access to:
   - Gmail or your email account (for sending confirmations, follow-ups, and document reminders)
   - Slack (for daily briefs and urgent alerts)
   
   Please connect each integration now. Let me know when you're ready and I'll guide you through it."

## After collecting all answers

1. Write the user's configuration to `config.json` at the workspace root using this structure:

```json
{
  "agent": "listing-showing-coordinator",
  "configuredAt": "<ISO timestamp>",
  "user": {
    "name": "<user's name>",
    "brokerage": "<brokerage or team name>",
    "marketType": "<residential | commercial | both>",
    "geography": "<market or region>"
  },
  "integrations": {
    "crm": "<CRM or MLS system name, or 'manual'>",
    "email": "connected",
    "slack": "connected"
  },
  "preferences": {
    "responseTone": "<professional | conversational>",
    "postShowingFollowUpCadence": {
      "sameDay": true,
      "followUpDays": [<day numbers, e.g. 3>]
    },
    "documentChaseSLADays": <number>
  },
  "slack": {
    "dailyBriefChannel": "<channel name>",
    "urgentAlertsChannel": "<channel name>"
  }
}
```

2. Append the following block to the `## Your context` section of `CLAUDE.md`, replacing any existing placeholder comment:

```
**Agent:** <user name> at <brokerage>
**Market:** <market type> — <geography>
**CRM/MLS:** <system name>
**Response tone:** <professional/formal | friendly/conversational>
**Post-showing follow-up cadence:** same-day thank-you + <N>-day check-in
**Document-chase SLA:** <N> days after due date before first reminder
**Daily brief channel:** <Slack channel>
**Urgent alerts channel:** <Slack channel>
**Integrations connected:** Email, Slack
```

3. Confirm setup is complete. Tell the user:
   - Their configuration has been saved.
   - The agent is ready to coordinate listings and showings.
   - Suggest the first action: "Try asking: *Show me all active listings and any showing requests that came in today.*"
