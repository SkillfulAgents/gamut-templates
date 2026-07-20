> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/legal-compliance/conflict-checker)** — one-click deploy, no setup.

# Conflict Checker (Legal Intake)

Automates conflict-of-interest checks for new matter intake. When a client or matter is submitted, the agent searches your firm's internal systems and public registries, categorizes findings by severity (clear / potential / hard conflict), drafts waiver language for consentable conflicts, and delivers a structured report to the requesting attorney — turning a multi-day manual process into same-day turnaround.

**Relevant subsegments: LAWF**

---

## What it does

1. **Accepts intake** — client name, adverse parties, matter type, and referring attorney
2. **Searches firm systems** — practice management system, conflict database, document management
3. **Searches public registries** — court dockets, bar websites, corporate registries, sanctions lists (browser-driven)
4. **Categorizes findings** — Clear / Potential conflict (needs review) / Hard conflict (blocked)
5. **Drafts waiver language** — consent letter templates for consentable (Tier 2) conflicts
6. **Delivers the report** — to the requesting attorney and any configured secondary recipients; posts a summary to Slack; sends urgent alerts for hard conflicts

---

## Systems supported

| Category | Examples |
|----------|---------|
| Practice management | Clio, iManage, NetDocuments, Filevine, MyCase, custom database, spreadsheet |
| Document management | iManage, NetDocuments, SharePoint |
| Conflict database | Built-in to PM system, standalone conflicts software, spreadsheet |
| Public registries | PACER, state court portals, Secretary of State sites, OFAC, bar websites |
| Notifications | Slack |

---

## Setup

Run the `agent-onboarding` skill to configure the agent for your firm. It will ask about your:

- Firm name and size
- Practice management and conflict tracking systems
- Matter types / practice areas
- Severity tier labels and consent/waiver policy
- Jurisdiction(s) for rules of professional conduct
- Report recipients (requesting attorney, conflicts committee, GC)
- Slack channels for reports and hard-conflict alerts

Configuration is saved to `CLAUDE.md` and `.claude/config.json`.

---

## First task

> Run a conflict check for new matter: client is Acme Corp, adverse party is Smith Industries, matter type is commercial litigation.

---

## Pattern

**Vertical — NON-TECH.** Serves law firms of all sizes: solo practitioners, boutiques, mid-size, and large firms.

---

## Notes

- The agent surfaces and categorizes potential conflicts; the supervising attorney makes the final determination.
- Public registry searches are best-effort and should not be the sole basis for a clearance decision.
- Tier 3 (hard conflict) findings require attorney review before any matter proceeds.
- Waiver language generated is a starting template only and should be reviewed by a qualified attorney before use.
