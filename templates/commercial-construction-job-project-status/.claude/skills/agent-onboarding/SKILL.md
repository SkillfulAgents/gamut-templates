---
name: agent-onboarding
---

Welcome - let's configure your Job / Project Status agent for your construction operation. This takes about 5 minutes. Your answers are saved so the agent knows which systems to pull from, what risk thresholds to apply, and who receives the daily brief.

Please answer the following questions. You can answer all at once or one at a time.

1. **Company basics** - What is your company name, and how would you describe your work? (For example: commercial GC, CM at risk, specialty contractor, or mixed.) How many active projects do you typically run at once?

2. **Project management system** - Do you use Procore? If so, which Procore modules are active on your projects (Schedule, Project Financials, RFIs, Submittals, Daily Logs, Change Management)?

3. **Accounting system** - Which accounting/cost system do you use? For example: Sage 300 CRE, Viewpoint Vista, Foundation, or other. This is the source for budget and cost-at-completion data.

4. **Schedule system** - How do you manage the construction schedule? Procore Schedule, Primavera P6, Microsoft Project, or a combination? Are schedules linked to Procore milestones?

5. **Risk thresholds** - What thresholds should trigger a flag? For example: how many days of schedule slip before it's worth flagging? What budget overrun percentage? How many days past due for an RFI response?

6. **Project types** - What kinds of projects does your firm typically run? (For example: commercial TI, ground-up office, industrial, public works, multifamily, healthcare.) This helps calibrate what "normal" looks like.

7. **Brief delivery** - Who should receive the daily ops brief and at what time? Please provide names and email addresses (and a Slack channel if applicable).

---

## After collecting answers

Save the configuration to `config.json` at the workspace root:

```json
{
  "company": {
    "name": "",
    "type": "",
    "typicalActiveProjects": null
  },
  "systems": {
    "projectManagement": "Procore",
    "procoreModules": [],
    "accounting": "",
    "scheduleSystem": ""
  },
  "projectTypes": [],
  "riskThresholds": {
    "scheduleSlipDays": 5,
    "budgetOverrunPct": 5,
    "rfiAgeDays": 10,
    "submittalLeadDays": 14,
    "staleLogDays": 7
  },
  "briefRecipients": [],
  "briefTime": "07:00"
}
```

Then update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-English paragraph summarizing the company name, work type, systems in use, risk thresholds, and brief delivery details.

Once both files are saved, confirm setup is complete and suggest a first task: "You're all set. To start, ask me to 'run the morning ops brief' and I'll pull your active jobs from Procore and give you today's status."
