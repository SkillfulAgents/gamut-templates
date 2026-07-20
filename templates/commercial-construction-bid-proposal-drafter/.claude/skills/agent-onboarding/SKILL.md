---
name: agent-onboarding
---

# Agent Onboarding

Welcome to the Bid / Proposal Drafter for commercial construction and general contracting. This onboarding configures the agent with your company's systems, credentials, and standards so it can produce accurate first-pass proposal packages without manual setup on every bid. Ask the following questions in order, then save the config and update the agent's context.

---

## Questions to ask

Ask the following questions in order, waiting for each answer before proceeding. If the user skips a question, record the value as `null` and note it as a gap.

**1. Company name, license numbers, and project types**
"What is your company's legal name as it should appear on proposals, and what are your contractor license number(s) and the state(s) they are issued in? Also, what are your primary project types - for example: commercial tenant improvement, ground-up commercial, industrial, healthcare, multifamily, or a mix?"

**2. Geographic markets**
"What geographic markets do you typically bid in? (e.g., Greater Chicago metro, Pacific Northwest, statewide Texas) List any markets you bid in regularly."

**3. Estimating and project management systems**
"Which of the following systems does your team use? Check all that apply: Procore, Sage 300 CRE, Viewpoint Vista, BuildingConnected. Are these systems connected to this Gamut workspace, or will the agent need to work from manually provided data?"

**4. Past project records**
"Where are your past project reference sheets, project photos, and completion data stored? For example: Procore project records, a shared drive folder, a proposals folder, or a CRM. Provide the system name and any folder path or identifier needed to access them."

**5. Subcontractor database**
"Where does your team track preferred and prequalified subcontractors? For example: Procore's subcontractor network, a BuildingConnected contact database, a spreadsheet, or a combination. How is the approved/prequalified status tracked?"

**6. Proposal structure defaults**
"What sections does your standard proposal typically include? For example: cover letter, scope of work, proposed schedule, project team bios, project references, insurance and bonding summary, qualifications and exclusions. List them in the order you normally present them."

**7. Proposal reviewers**
"Who reviews proposals before they go out to owners? List names and roles - for example: lead estimator, project manager, principal in charge. Note whether any reviewer has final approval authority."

---

## After collecting answers

1. Save all answers to `.claude/config.json` using the following structure:

```json
{
  "companyName": "",
  "licenseNumbers": [],
  "projectTypes": [],
  "markets": [],
  "systems": {
    "procore": { "connected": false, "companyId": "" },
    "sage300": { "connected": false, "companyCode": "" },
    "viewpointVista": { "connected": false },
    "buildingConnected": { "connected": false }
  },
  "projectRecordStorage": "",
  "subDatabase": "",
  "proposalSections": [],
  "reviewers": []
}
```

2. Update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-text summary of the configuration. Write it as a bulleted list covering: company name and license numbers, project types, geographic markets, connected systems and any access notes, project record storage location, subcontractor database location, standard proposal section order, and reviewers with roles.

3. Confirm to the user: "Onboarding complete. Your configuration has been saved. To start a bid, paste or upload the RFP document, bid invite, or BuildingConnected notification and I will produce a first-pass proposal draft with a prioritized missing-information checklist."
