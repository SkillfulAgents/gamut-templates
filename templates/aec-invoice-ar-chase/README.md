> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/invoice-ar-chase/aec-invoice-ar-chase)** — one-click deploy, no setup.

# Architecture/Engineering/Design - Invoice & AR Chase

Architecture, engineering, and design firms run on project fees - but getting paid on time is a constant challenge. Clients sit on invoices, draw requests get lost in approval chains, and chasing them can feel like it puts the relationship at risk. This agent handles AR follow-up in the principal's voice: drafting outreach, escalating by aging tier, and delivering a weekly cash and AR digest so principals and project managers always know where the money stands.

## Who this is for

AEC practices of any size - architecture firms, civil and structural engineering studios, MEP consultants, interior designers, and land planners - that bill on a project or retainer basis. It is especially useful for firms managing multiple simultaneous projects with multiple clients, where AR follow-up falls through the cracks or gets deprioritized to protect relationships. Works with Deltek Vision/Vantagepoint, BQE Core, QuickBooks, and Ajera.

## What it does

1. **Identifies and ages open AR** - Pulls open invoices and AIA draw requests from your project accounting system, groups them by client and aging bucket (0-30, 31-60, 61-90, 90+ days), and flags retainage and disputed amounts separately.

2. **Drafts tiered outreach in the principal's voice** - Writes client-facing emails that match the right tone to the aging tier: warm and collegial for early reminders, increasingly direct for older balances, and formal demand language for critical accounts - all ready for the principal to review and send.

3. **Escalates with precision** - At 61+ days, routes outreach to both the client's PM and their AP department. At 90+ days, drafts a formal demand letter with a clear deadline and next steps, flagged for principal approval before sending.

4. **Flags lien and stop-notice deadlines** - For construction-phase services, notes when preliminary notice or lien rights windows are approaching so the firm can act before rights expire.

5. **Delivers a weekly cash and AR digest** - Every Monday, generates a practice-wide summary: total AR by bucket, largest open balances, accounts that changed tiers, and projected cash receipts for the week. Formatted for a principal briefing or partner meeting.

## Key integrations

- **Deltek Vision / Vantagepoint** - Primary project accounting source for AR aging, invoice history, and billing notes on each project.
- **BQE Core** - Alternative project accounting and time-billing platform; pulls open invoices, client records, and project billing data.
- **QuickBooks** - Used for payment reconciliation and customer-level memo logging, particularly in firms running a dual-system setup alongside Deltek or BQE Core.
- **Ajera** - Christensen Bros. / Axium Ajera (Deltek-family) project accounting; pulls AR aging and project billing records for firms running Ajera as their primary system.

## Getting started

1. **Import this workspace** into Gamut using the workspace import option. The agent and its onboarding skill will load automatically.
2. **Run the agent-onboarding skill** by typing `run agent-onboarding` in the chat. The skill will ask you a short set of questions about your firm, your billing systems, and your AR policies.
3. **Give the agent its first task** - for example: "Pull all invoices past due more than 30 days and draft first-touch emails for each one" or "Generate this week's AR digest."

## Configuration

After onboarding, the agent stores your settings in `.claude/skills/agent-onboarding/config.json` and updates the `## Your context` section of `CLAUDE.md` with a plain-English summary of your firm's setup. You can edit either file directly to adjust principal names, aging thresholds, or system credentials.

---

Relevant subsegments: AEC
