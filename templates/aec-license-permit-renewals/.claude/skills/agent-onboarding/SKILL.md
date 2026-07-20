---
name: agent-onboarding
---

# Agent Onboarding

You are running the onboarding flow for the Architecture/Engineering/Design - License / Permit / Cert Renewals agent. Your goal is to collect the configuration needed to set up compliance tracking for this firm. Work through the questions below conversationally - ask one or two at a time, confirm answers before moving on, and save the completed config when all questions are answered.

---

## Questions to ask

**1. Firm name, disciplines, and jurisdictions**
Ask: What is your firm's name? What disciplines does the firm practice (architecture, civil engineering, structural, MEP, landscape architecture, multi-discipline, etc.)? And which states or jurisdictions does the firm currently practice in - including states where you have active projects or hold firm-level licenses or COAs?

**2. Firm management system**
Ask: Which system does the firm use to manage projects and employee records? Options:
- Deltek Vision
- Deltek Vantagepoint
- BQE Core
- Other (ask them to name it)

Do you have API access or export credentials available for that system?

**3. License types to track**
Ask: Which types of licenses and credentials does the firm need to track? Select all that apply:
- Individual PE licenses (professional engineer, by state)
- Individual architect licenses (RA, AIA, NCARB)
- Firm registrations / Certificates of Authorization by state
- Certificates of insurance (COI) - general liability, professional liability/E&O, workers comp, umbrella
- Professional liability insurance at the firm level
- Business operating permits
- DBE/MBE/WBE or other specialty certifications
- LEED credentials (individual or firm)
- OSHA certifications
- Other specialty credentials (ask them to list)

**4. Where credentials are tracked today**
Ask: Where does the firm currently track staff credentials and license expiration dates? Options include a spreadsheet, a shared drive folder, fields inside Deltek or BQE Core, a dedicated compliance system, or no formal tracking at the moment. This helps determine what can be imported vs. what needs to be entered manually.

**5. Continuing education requirements**
Ask: Do any staff members have recurring continuing education deadlines tied to their licenses? For example, PE licenses require PDH credits per renewal cycle, AIA membership requires LU/HSW hours, and some LEED credentials require continuing education. If yes, which license types carry CE requirements, and do you know the current cycle and hours required?

**6. Alert recipients**
Ask: Who should receive renewal alerts and compliance reports? For each of the following roles, provide a name and email address (or note if the same person covers multiple roles):
- The license holder themselves (for individual credentials)
- The HR or compliance contact who manages firm-level renewals
- The principal or partner responsible for licensing decisions
- Any operations or administrative staff who track renewals day-to-day

**7. Compliance report format**
Ask: When you produce compliance summary reports - for example, for an internal quarterly review, a lender or bonding company, a client requesting proof of insurance, or an insurance audit - what format works best? Options include plain text for email, a structured list suitable for PDF, a CSV export for spreadsheet review, or a mix depending on the audience.

---

## After collecting answers

Save all answers to `.claude/config.json` in this structure:

```json
{
  "firmName": "",
  "disciplines": [],
  "jurisdictions": [],
  "firmSystem": "",
  "firmSystemApiAccess": false,
  "licenseTypes": [],
  "credentialStorage": "",
  "ceRequirements": false,
  "ceDetails": "",
  "alertRecipients": {
    "licenseHolder": true,
    "hrCompliance": { "name": "", "email": "" },
    "principalLicensing": { "name": "", "email": "" },
    "operationsContact": { "name": "", "email": "" }
  },
  "alertThresholds": {
    "initialNoticeDays": 90,
    "actionRequiredDays": 60,
    "urgentDays": 30,
    "criticalDays": 14
  },
  "reportFormat": ""
}
```

Then update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-text summary:

```
**Firm:** [name]
**Disciplines:** [list]
**Jurisdictions:** [list of states/jurisdictions]
**Firm system:** [Deltek Vision / Vantagepoint / BQE Core] (API access: yes/no)
**License types tracked:** [list]
**Credential storage today:** [location or "none"]
**CE requirements:** [yes/no] - [summary if yes]
**Alert recipients:** HR/Compliance: [name, email] | Principal: [name, email] | Operations: [name, email]
**Alert thresholds:** 90 / 60 / 30 / 14 days
**Report format:** [plain text / PDF-ready / CSV / mixed]
```

Confirm setup is complete and tell the user their next step is to provide a starting credential list - either an export from their ERP, an existing spreadsheet, or a manual list - so the agent can populate the compliance registry. They can also ask: "Show me everything expiring in the next 90 days" to begin their first compliance review.
