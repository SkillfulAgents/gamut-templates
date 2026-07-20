---
name: agent-onboarding
---

# Agent Onboarding - Agriculture/AgriBusiness License / Permit / Cert Renewals

Welcome. This onboarding session will configure your compliance renewal tracking agent for your agricultural operation. I will ask a few questions about your credential inventory, connected systems, team structure, and alert preferences. Your answers will be saved so the agent can start tracking renewals and sending the right nudges to the right people right away.

Please answer each question as specifically as you can. You can always update your configuration later by editing `config.json` or the `## Your context` section in `CLAUDE.md`.

---

**Question 1: Operation overview**
What type of agricultural operation are you setting up this agent for? Include the primary commodity or product type (e.g., row crops, produce, livestock, dairy, specialty crops) and roughly how many locations or parcels you manage compliance across.

**Question 2: Credential inventory**
What categories of licenses, permits, and certifications does your operation currently hold or need to track? Select all that apply and add any not listed:
- Pesticide applicator licenses (state-issued, by individual)
- Water use or irrigation permits
- Food safety certifications (GAP, GHP, FSMA Produce Safety Rule)
- Organic certification (USDA NOP)
- Equipment inspection records (sprayers, scales, storage facilities)
- Restricted material permits
- Air quality or burn permits
- Other: describe

**Question 3: Connected systems**
Which farm management software and ERP systems does your operation use? Please name the specific platforms (e.g., Granular, AgriWebb, Trimble Ag, FarmLogs for farm management; SAP, Dynamics 365, AgriForce for ERP) and note whether you have API access or will be uploading records manually.

**Question 4: USDA and state portal access**
Which state(s) does your operation hold permits or licenses in? List each state and whether you currently have login credentials for that state's agriculture department portal. Also note whether you have a USDA eAuthentication account for federal programs (organic, GAP/GHP, APHIS permits).

**Question 5: Team and escalation contacts**
Who should receive renewal alerts? For each role below, provide a name and email (or confirm they are not applicable):
- Primary compliance contact (first to receive all alerts)
- Operations lead or compliance officer (escalation at 30 days)
- Executive or owner (escalation at 14 days and post-expiration)
- Any additional credential holders who should receive personal reminders for their individual licenses

**Question 6: Alert preferences**
How would you like renewal alerts delivered? Options: email, SMS, Slack or Teams message, task created in ERP, or a combination. Also confirm whether the default alert schedule (120/60/30/14 days) works for your operation or if you need adjustments for specific credential types.

**Question 7: Document storage**
Where should renewed credentials and compliance records be stored? Confirm the folder path or vault location in your farm management software or ERP, or provide a shared drive location if documents are managed outside those systems.

**Question 8: Audit and reporting needs**
How often do you need a compliance status report, and who should receive it? Also note whether you have any upcoming audits, buyer contract reviews, or lender inspections that require an audit-ready compliance summary on a specific date.

---

## After collecting answers

Once the user has answered all questions, do the following:

### 1. Write config.json

Create a `config.json` file at the workspace root with this structure, populated with the user's answers:

```json
{
  "operation": {
    "name": "",
    "type": "",
    "commodities": [],
    "locations": []
  },
  "credentialCategories": [
    "pesticide_applicator_licenses",
    "water_use_permits",
    "food_safety_certifications",
    "organic_certification",
    "equipment_inspections",
    "other"
  ],
  "systems": {
    "farmManagement": {
      "platform": "",
      "apiAccess": true
    },
    "erp": {
      "platform": "",
      "apiAccess": true
    },
    "usdaPortal": {
      "eAuthAccount": true,
      "programs": []
    },
    "statePortals": [
      {
        "state": "",
        "portalUrl": "",
        "hasCredentials": true
      }
    ]
  },
  "alertContacts": {
    "primaryCompliance": {
      "name": "",
      "email": ""
    },
    "operationsLead": {
      "name": "",
      "email": ""
    },
    "executive": {
      "name": "",
      "email": ""
    },
    "credentialHolders": []
  },
  "alertSchedule": {
    "daysOut": [120, 60, 30, 14],
    "channels": [],
    "postExpirationProtocol": "critical_escalation"
  },
  "documentStorage": {
    "platform": "",
    "folderPath": "",
    "versionControl": true
  },
  "reporting": {
    "frequency": "weekly",
    "recipients": [],
    "nextAuditDate": null
  }
}
```

### 2. Update CLAUDE.md

Open `CLAUDE.md` and replace the `<!-- Filled in during onboarding -->` comment under `## Your context` with a plain-English summary of the operation's setup. Include: operation name and type, credential categories being tracked, connected systems and access method, alert contacts and escalation chain, alert delivery channels, document storage location, and any upcoming audit dates. Keep it concise - 150 to 250 words.

### 3. Confirm setup and suggest first task

Tell the user their agent is configured and ready. Then suggest one of the following first tasks based on what they told you:

- If they have a known upcoming audit: "Generate an audit-ready compliance summary for [date]."
- If they have never done a full credential sweep: "Pull all credential records from [farm management platform] and build the initial compliance register."
- Otherwise: "Show me everything expiring in the next 90 days and flag any that are already past due."
