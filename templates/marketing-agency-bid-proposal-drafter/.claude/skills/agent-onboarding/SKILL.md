---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user to the Marketing/Creative Agency - Bid / Proposal Drafter agent. Explain that you are going to ask a few quick questions to configure the agent for their specific agency — its voice, deal history, and proposal workflow — and then it will be ready to turn incoming RFPs into polished first-pass proposals.

Ask the following questions. You may present them all together in a single message:

1. **Agency name and voice** — What is the name of your agency, and how would you describe your proposal voice? (e.g., "bold and direct", "strategic and consultative", "creative-first" — a few words is enough; this sets the tone for all drafted proposals)
2. **HubSpot pipeline setup** — What is the name of your HubSpot pipeline for new business deals, and what are the deal stage names you use for "proposal drafted" and "proposal sent"? (If you are not sure of the exact names, describe them and the agent will match.)
3. **Asana proposals project** — What is the name of the Asana project where proposal tasks should be created? And who is the default account lead to assign tasks to when no deal owner is identified in HubSpot?
4. **Standard proposal structure** — Do you want to use the default proposal structure (executive summary / scope / approach / team / timeline / investment / why-us / next steps), or do you have a different section order or sections you always include or exclude?
5. **Internal asset library** — Where are your boilerplate proposal sections, team bios, case study summaries, and portfolio links stored? (Google Drive folder URL, Notion page, a local file path, or "none yet" — be specific so the agent knows where to pull reusable content)
6. **Pricing and deal norms** — What is the minimum deal size you would typically bid on, and what dollar threshold should trigger a high-value flag for principal review? (e.g., "minimum $5K, flag anything over $75K")
7. **Follow-up window** — How many business days after sending a proposal should the agent set a follow-up reminder in HubSpot? (default is 3 business days)

## After collecting answers

Write a `config.json` file at `.claude/skills/agent-onboarding/config.json` with this structure, filled in from the answers:

```json
{
  "agencyName": "<agency name>",
  "agencyVoice": "<voice description>",
  "hubspot": {
    "pipelineName": "<pipeline name>",
    "proposalDraftedStage": "<stage name>",
    "proposalSentStage": "<stage name>"
  },
  "asana": {
    "proposalsProject": "<project name>",
    "defaultAccountLead": "<name or email>"
  },
  "proposalStructure": "default",
  "assetLibraryUrl": "<URL or path, or null>",
  "minimumDealSize": 0,
  "highValueThreshold": 0,
  "followUpWindowDays": 3
}
```

If the agency uses a custom proposal structure, replace `"default"` in `proposalStructure` with an ordered array of section names (e.g., `["Executive Summary", "Scope", "Approach", "Timeline", "Investment", "Next Steps"]`).

Then update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-English summary:

```
## Your context

**Agency:** [Agency Name]
**Voice:** [voice description]
**HubSpot pipeline:** [pipeline name] — proposal drafted stage: [stage] / proposal sent stage: [stage]
**Asana proposals project:** [project name] — default account lead: [name]
**Proposal structure:** [default or custom section list]
**Asset library:** [URL/path or "not configured"]
**Deal sizing:** minimum $[X] / high-value flag at $[Y]
**Follow-up window:** [N] business days after proposal sent
```

Confirm that setup is complete and the agent is ready to use. Then give the account lead their first task prompt to get started:

> "Here's an RFP we just received — draft a first-pass proposal and flag everything we need to confirm before sending."
