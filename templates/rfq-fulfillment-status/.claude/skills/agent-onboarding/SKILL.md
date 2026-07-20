---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user and explain that you'll ask a few setup questions to configure the RFQ / Order & Fulfillment Status agent for their operations. Tell them it will take about 5 minutes and that their answers will be saved so the agent is ready to use immediately after.

## Interview questions

Ask these questions conversationally, one topic at a time. Do not dump all questions at once.

### 1. User identity
- What's your name?
- What company are you at?
- What's your role? (e.g., ops manager, buyer, logistics coordinator, supply chain analyst)

### 2. ERP / order management system
- Which ERP or order management system does your team use? (e.g., NetSuite, SAP Business One, Epicor, Acumatica, spreadsheet-based, other)
- How should the agent query it? Options:
  - **API / connected account** — ask them to connect via the available integrations
  - **CSV export** — they'll upload a periodic export; confirm cadence (daily, on-demand)
  - **Manual input** — they'll paste or describe order data when running the agent
- If API: walk them through connecting the account and confirm which data objects are accessible (POs, RFQs, shipments, backorders).

### 3. SLA thresholds
- How many days after a PO is issued should you flag it if the supplier hasn't acknowledged it? (Default: **2 days** — accept their number or confirm the default.)
- How many days without a tracking update before a shipment is flagged as stalled? (Default: **3 days** — accept their number or confirm the default.)
- How many days past the expected delivery date before a backordered line item is escalated? (Default: **7 days** — accept their number or confirm the default.)

### 4. Alerts and digest routing
- Which Slack channel should the daily ops digest go to? (Ask for the channel name, e.g., #ops-daily or #supply-chain)
- Who is the escalation contact for critical exceptions (freight holds, high-value backorders)? (Name and Slack handle or email)

### 5. Email for supplier outreach
- Connect the email account you use for supplier communications so the agent can send follow-up emails on your behalf.
- Confirm: should the agent send follow-up emails automatically when a PO hits the SLA threshold, or should it draft them for your review first?

### 6. Slack connection
- Connect your Slack workspace so the agent can post the daily digest and exception alerts to the channel you specified.

## After the interview

Once you have all the answers:

1. Write the collected context into the `## Your context` section of `CLAUDE.md` using this structure:

```
## Your context

**User:** [name], [role] at [company]

**ERP / Order system:** [system name]
**Data access method:** [API / CSV export / manual input]

**SLA thresholds:**
- PO acknowledgment: flag after [N] days with no supplier response
- Shipment tracking: flag after [N] days with no update
- Backorder escalation: flag after [N] days past expected delivery

**Daily digest channel:** [#channel-name]
**Escalation contact:** [name, Slack handle or email]

**Supplier email account:** [email address or connected account name]
**Email send mode:** [automatic / draft for review]
```

2. Write a `config.json` file to `/workspace/config.json` with this structure:

```json
{
  "user": {
    "name": "",
    "company": "",
    "role": ""
  },
  "erp": {
    "system": "",
    "accessMethod": "api | csv | manual"
  },
  "sla": {
    "poAcknowledgmentDays": 2,
    "shipmentStaleDays": 3,
    "backorderEscalationDays": 7
  },
  "slack": {
    "digestChannel": "",
    "escalationContact": ""
  },
  "email": {
    "account": "",
    "sendMode": "automatic | draft"
  }
}
```

Fill in all values from the interview answers.

3. Confirm setup is complete and suggest the first action:

> "You're all set! Try: **Show me all open POs that haven't been acknowledged in 2+ days and draft supplier follow-ups.**"
