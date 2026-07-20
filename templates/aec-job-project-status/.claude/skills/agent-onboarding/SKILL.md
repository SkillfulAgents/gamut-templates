---
name: agent-onboarding
---

# Agent Onboarding

You are running the onboarding flow for the Architecture/Engineering/Design - Job / Project Status agent. Your goal is to collect the configuration needed to set up the daily ops brief for this firm. Work through the questions below conversationally - ask one or two at a time, confirm answers before moving on, and save the completed config when all questions are answered.

---

## Questions to ask

**1. Firm basics**
Ask: What is your firm's name, what is your primary discipline (architecture, civil engineering, MEP, structural, multi-discipline, etc.), and roughly how many active projects does the firm carry at any given time?

**2. Project management and accounting system**
Ask: Which system does the firm use as its primary project management and financial platform? Options:
- Deltek Vision
- Deltek Vantagepoint
- BQE Core
- Other (ask them to name it)

Note which system they use and whether they have API access or export credentials available.

**3. Procore usage**
Ask: Do you also use Procore for project management? If yes, which Procore modules are active - schedule, RFIs, submittals, change orders, or others?

**4. Daily ops review today**
Ask: What does your daily or weekly project review look like today - who attends, what data sources do you pull from, and what typically gets flagged? This helps calibrate what the brief should emphasize.

**5. Risk thresholds**
Ask: What thresholds matter most for flagging a project at risk? Suggest defaults and confirm:
- Schedule slip: how many days behind before flagging? (default: 7 days)
- Budget overrun: what percentage over budget before flagging? (default: 10%)
- Unbilled WIP: what dollar amount of unbilled work triggers a flag? (default: $15,000)
- Inactivity: how many days with no activity before a project is flagged as stalled? (default: 21 days)
- Approval stall: how many days for a client or agency approval to sit open before flagging? (default: 14 days)

**6. Brief recipients and delivery time**
Ask: Who should receive the daily ops brief, and at what time each morning? Provide names and email addresses (or a Slack channel) for everyone who should be on the distribution.

**7. Project phases**
Ask: What project phases does your firm use? (These vary by discipline - e.g., architecture firms typically use SD/DD/CD/CA/Closeout; civil/infrastructure firms may use different phase names.) List the phases so the agent can reference them correctly when flagging milestone gaps.

---

## After collecting answers

Save all answers to `.claude/config.json` in this structure:

```json
{
  "firm": "",
  "discipline": "",
  "activeProjectCount": "",
  "system": "",
  "systemApiAccess": false,
  "procore": false,
  "procoreModules": [],
  "riskThresholds": {
    "scheduleSlipDays": 7,
    "budgetOverrunPct": 10,
    "unbilledWipDollars": 15000,
    "inactivityDays": 21,
    "approvalStallDays": 14
  },
  "briefRecipients": [],
  "briefTime": "07:00",
  "briefDelivery": "email",
  "briefSlackChannel": "",
  "projectPhases": []
}
```

Then update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-text summary:

```
**Firm:** [name] - [discipline]
**Active projects:** approx. [count]
**Primary system:** [Deltek Vision / Vantagepoint / BQE Core]
**Procore:** [yes/no] - modules: [list]
**Risk thresholds:** Schedule slip [N] days, budget overrun [X]%, unbilled WIP $[amount], inactivity [N] days, approval stall [N] days
**Brief recipients:** [names and emails or Slack channel]
**Brief time:** [time]
**Project phases:** [list]
```

Confirm setup is complete and tell the user they can trigger the first brief by asking: "Run the daily ops brief."
