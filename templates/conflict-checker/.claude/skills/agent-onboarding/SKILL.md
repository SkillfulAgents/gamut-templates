---
name: agent-onboarding
---

# Agent Onboarding

Welcome to the Conflict Checker agent. This skill configures the agent for your law firm by collecting the information needed to connect your systems and calibrate the conflict-check workflow.

## What this skill does
Interviews you with a short set of questions, then writes your answers to:
- `CLAUDE.md` — updates the `## Your context` section with firm-specific configuration
- `.claude/config.json` — stores structured configuration values

## Interview

Work through the questions below **one section at a time**. Ask all questions in a section together, wait for the user's answers, then move to the next section.

---

### Section 1 — Firm basics

Ask:
1. What is your name and role at the firm?
2. What is the name of your firm?
3. How would you describe the firm's size?
   - Solo (1 attorney)
   - Boutique (2–15 attorneys)
   - Mid-size (16–100 attorneys)
   - Large (100+ attorneys)

---

### Section 2 — Conflict tracking and practice management

Ask:
1. What practice management or matter management system does the firm use? (e.g., Clio, iManage, NetDocuments, Filevine, MyCase, a custom database, or a spreadsheet — or "none / manual")
2. How are conflicts currently tracked? For example:
   - Built into the practice management system
   - A separate conflicts database or software (name it if known)
   - A spreadsheet or shared document
   - Manually, no formal system
3. Does the firm use a separate document management system (e.g., iManage, NetDocuments, SharePoint)? If yes, which one?

---

### Section 3 — Practice areas and matter types

Ask:
1. What types of matters does the firm primarily handle? (Select all that apply, or describe freely.)
   - Corporate / transactional
   - Commercial litigation
   - Family law / domestic relations
   - Real estate
   - Intellectual property
   - Employment / labor
   - Regulatory / government
   - Criminal defense
   - Estate planning / probate
   - Other (please describe)

   *(This shapes how deep the agent searches public court records and registries.)*

---

### Section 4 — Severity tiers and waiver policy

Ask:
1. Do you want to use the default three-tier severity system (Clear / Potential conflict — needs review / Hard conflict — blocked), or would you like to customize the tier names or add tiers?
2. What is the firm's default policy on consented/waived conflicts?
   - Consent is pursued whenever the conflict is consentable under applicable rules
   - Consent is only pursued for long-standing clients or at partner discretion
   - The firm generally declines matters with any conflict, even potential ones
   - Other (please describe)
3. Which jurisdiction(s) does the firm primarily practice in? (Used to reference applicable rules of professional conduct — e.g., state-specific Model Rule variations.)

---

### Section 5 — Report recipients

Ask:
1. Who should receive the completed conflict report?
   - Requesting attorney only
   - Requesting attorney + a conflicts committee or designated partner
   - Requesting attorney + General Counsel
   - Other (please describe)
2. For Tier 3 (hard conflict / blocked) findings, should an urgent alert go to anyone beyond the standard recipients? If yes, who?

---

### Section 6 — Slack

Ask:
1. What Slack channel should completed conflict reports be posted to? (e.g., `#conflicts`, `#legal-intake`)
2. Is there a separate channel for urgent hard-conflict alerts, or should those go to the same channel?

Then guide the user to connect Slack:
> To post reports and alerts to Slack, please connect your Slack workspace. Run `/connect slack` or follow the Gamut integration setup flow, then confirm here once Slack is connected.

Wait for the user to confirm Slack is connected before proceeding.

---

## Writing configuration

Once all sections are complete, do the following:

### Update CLAUDE.md

Replace the `## Your context` placeholder at the bottom of `CLAUDE.md` with a filled-in context block. Example structure (adapt to the user's actual answers):

```markdown
## Your context

**Firm:** [Firm name]
**Configured by:** [Name, role]
**Firm size:** [Solo / Boutique / Mid-size / Large]

### Systems
- **Practice management / conflict tracking:** [System name and how conflicts are tracked]
- **Document management:** [System name, or "None"]

### Practice areas
[Comma-separated list of matter types the firm handles]

### Severity tiers
| Tier | Label | Meaning |
|------|-------|---------|
| 1 | Clear | No conflicts found; matter may proceed |
| 2 | [Tier 2 label] | [Description] |
| 3 | [Tier 3 label] | [Description] |

**Waiver/consent policy:** [Firm's policy]
**Primary jurisdiction(s):** [Jurisdiction(s)]

### Report distribution
- **Standard recipients:** [Who receives completed reports]
- **Hard-conflict alert recipients:** [Who receives urgent Tier 3 alerts]

### Slack
- **Reports channel:** [#channel-name]
- **Hard-conflict alerts channel:** [#channel-name or "same as reports"]
```

### Write .claude/config.json

Create or update `.claude/config.json` with the structured values:

```json
{
  "firm_name": "",
  "firm_size": "",
  "practice_management_system": "",
  "conflict_tracking_method": "",
  "document_management_system": "",
  "practice_areas": [],
  "severity_tiers": {
    "1": "Clear",
    "2": "Potential conflict — needs review",
    "3": "Hard conflict — blocked"
  },
  "waiver_policy": "",
  "jurisdictions": [],
  "report_recipients": [],
  "hard_conflict_alert_recipients": [],
  "slack_reports_channel": "",
  "slack_alerts_channel": ""
}
```

Fill in all fields from the user's answers. For severity tiers, use the custom labels if the user provided them; otherwise use the defaults shown above.

---

## Completion message

Once CLAUDE.md and config.json are written, confirm setup is complete:

> Setup complete. The Conflict Checker is configured for **[Firm name]**.
>
> To run your first conflict check, try:
> **"Run a conflict check for new matter: client is Acme Corp, adverse party is Smith Industries, matter type is commercial litigation."**
>
> The agent will search your configured systems and public registries, categorize any findings, and deliver a tiered conflict report.
