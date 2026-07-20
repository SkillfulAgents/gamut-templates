---
name: agent-onboarding
---

Welcome - let's get your Bid / Proposal Drafter set up for your firm. This will take about five minutes. I'll ask a few questions about your practice, your systems, and how your proposals are typically structured. Your answers will be saved so the agent is ready to help you draft proposals without re-explaining your setup each time.

Please answer the following questions. You can answer all at once or one at a time.

1. **Firm basics** - What is your firm's full name, primary discipline (architecture, civil engineering, MEP, landscape, multi-discipline, etc.), and the geographic markets you typically pursue work in?

2. **Project management and accounting systems** - Which systems does your firm use to store project data and staff records? For example: Deltek Vision, Deltek Vantagepoint, BQE Core, Procore, a combination, or something else? Please include version if known (e.g. Vantagepoint 6.x).

3. **Proposal structure defaults** - What sections does your firm's standard proposal typically include? (For example: cover letter, executive summary, firm qualifications, relevant experience, project approach, team bios, fee schedule, references.) List them in the order you prefer.

4. **Past project records** - Where are your past project write-ups and metrics stored? Are they in Deltek/BQE project records, a shared drive folder, a separate qualifications database, or a mix? Roughly how many completed projects do you have on file?

5. **Fee schedule and rate structure** - Does your firm use a standard hourly rate schedule, a multiplier-based structure, or project-type-specific fee templates? Where are your current rate sheets stored (Deltek, BQE Core, a spreadsheet, etc.)?

6. **Typical proposal team** - What roles are usually included in a proposal team? (For example: principal-in-charge, project manager, project architect, technical specialist, subconsultant leads.) Are subconsultant bios typically sourced in-house or requested fresh each pursuit?

7. **Submission preferences and constraints** - Are there standing page limits, font/format standards, or firm style guidelines that should be applied to every proposal? Do you track pursuits in a bid log inside Procore, Deltek, or another tool?

8. **Common RFP types** - What procurement types does your firm most often respond to? (For example: public agency RFQs, private owner RFPs, design-build RFPs, federal A-E selection, municipal engineering contracts.) This helps the agent calibrate compliance language and tone.

---

## After collecting answers

Save the firm's configuration to `config.json` at the workspace root using the following structure:

```json
{
  "firm": {
    "name": "",
    "discipline": "",
    "markets": []
  },
  "systems": {
    "projectAccounting": "",
    "projectManagement": "",
    "bidTracking": "",
    "qualificationsDatabase": ""
  },
  "proposalDefaults": {
    "sectionOrder": [],
    "pageLimit": null,
    "formatStandards": ""
  },
  "feeSchedule": {
    "structure": "",
    "storageLocation": ""
  },
  "typicalTeam": {
    "roles": [],
    "subconsultantBioSource": ""
  },
  "pastProjects": {
    "storageLocation": "",
    "approximateCount": null
  },
  "rfpTypes": []
}
```

Then update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-English paragraph summarizing the firm's name, discipline, systems in use, typical proposal structure, fee approach, and any standing format constraints. Write it as a briefing for the agent, not as a list of config values.

Once both files are saved, confirm to the user that setup is complete and suggest a first task: "You're all set. To get started, paste or attach an RFP or RFQ and I'll parse it, pull relevant past projects from [system name], and draft a first-pass proposal with a missing-information checklist for your review."
