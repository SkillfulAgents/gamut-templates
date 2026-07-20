---
name: agent-onboarding
---

Welcome to the Restaurant/QSR License, Permit, and Cert Renewal agent. This skill will collect the details about your operation so the agent can track every credential you need, alert the right people at the right time, and generate audit-ready compliance summaries on demand.

This should take about 5-10 minutes. Your answers will be saved to `config.json` and summarized in the agent's `CLAUDE.md` so it is ready to work from day one.

Let's go through a few questions:

1. **Locations** - How many locations do you operate? For each location, what is the name, address, city, state, and county? (County matters because health department jurisdictions often differ from city or state lines.)

2. **Business type** - What type of food service operation is this? (For example: full-service restaurant, QSR/fast food, fast casual, bar or tavern, food truck, catering, or a mix.) Do any locations hold a liquor or beer-and-wine license?

3. **Current credential inventory** - What licenses and permits do you currently hold? For each, it helps to know: the credential type, issuing authority, license or permit number, expiration date, and the staff member responsible for renewal. If you have a spreadsheet or document tracking these, you can paste it here and the agent will parse it.

4. **Employee certification setup** - How do you track food handler cards and food safety certifications for staff? Are you using Toast POS, Square, or another system as your employee roster? Approximately how many active employees need food handler cards?

5. **Health department portals** - Which county or city health department portals do you use to check permit status or submit renewal applications? Please share the portal URL(s) for each jurisdiction you operate in.

6. **Renewal alert recipients** - Who should receive renewal alerts for each credential type? For example: the GM gets all alerts for their location; the owner or operator gets 30-day and 7-day escalations; a specific manager handles liquor license renewals. Describe your preferred escalation chain.

7. **Document storage** - Where do you store copies of your current permits and licenses? (Options include: a shared Google Drive folder, a Dropbox folder, physical binder, or no current system.) The agent can reference a folder link for each location if you have one.

8. **Upcoming renewals** - Are any credentials expiring in the next 90 days that need immediate attention? If so, list the credential, location, and expiration date so the agent can prioritize right away.

## After collecting answers

Use the answers above to write the following files:

### config.json

Create `.claude/config.json` in the workspace with this structure:

```json
{
  "business": {
    "name": "",
    "type": "",
    "has_liquor_license": false
  },
  "locations": [
    {
      "id": "loc_1",
      "name": "",
      "address": "",
      "city": "",
      "state": "",
      "county": "",
      "health_dept_portal": "",
      "document_storage_url": "",
      "gm_name": "",
      "gm_contact": ""
    }
  ],
  "credentials": [
    {
      "type": "",
      "issuing_authority": "",
      "license_number": "",
      "location_id": "",
      "expiration_date": "",
      "renewal_owner": "",
      "renewal_owner_contact": "",
      "document_url": ""
    }
  ],
  "integrations": {
    "toast_pos": {
      "enabled": false,
      "api_key": "",
      "location_ids": []
    },
    "square": {
      "enabled": false,
      "location_ids": []
    },
    "google_business": {
      "enabled": false,
      "profile_urls": []
    },
    "yelp": {
      "enabled": false,
      "business_ids": []
    }
  },
  "alert_thresholds_days": [90, 60, 30, 7],
  "escalation": {
    "day_90_recipients": [],
    "day_60_recipients": [],
    "day_30_recipients": [],
    "day_7_recipients": []
  }
}
```

Fill in every field from the answers collected above. Add one entry per location and one entry per known credential.

### Update CLAUDE.md

Add a plain-English summary under `## Your context` in `CLAUDE.md` covering:
- Business name, type, and number of locations
- Which credential types are in scope
- Which integrations are active (Toast, Square, Google, Yelp)
- Who receives alerts at each escalation tier
- Any credentials expiring within 90 days that need immediate action
- Where documents are stored

### Confirm setup and suggest first task

Once the files are written, tell the user:

"Setup is complete. Your [X] locations and [Y] credentials are now in the registry. Here are a few tasks to start with:

- 'Show me everything expiring in the next 60 days across all locations.'
- 'Generate an audit-ready compliance summary for [location name].'
- 'Which employees at [location] have food handler cards expiring this month?'
- 'Draft a renewal reminder for our liquor license at [location].'"
