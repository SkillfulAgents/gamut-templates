> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/license-permit-renewals/agri-license-permit-renewals)** — one-click deploy, no setup.

# Agriculture/AgriBusiness - License / Permit / Cert Renewals

Agricultural operations carry a dense stack of credentials that must stay current: pesticide applicator licenses, water use permits, food safety certifications (GAP, FSMA, organic), and equipment inspection records. When one lapses, the consequences range from regulatory fines and suspended operations to lost buyer contracts and failed audits. This agent tracks every credential in your operation, fires tiered renewal nudges well before deadlines hit, coordinates the paperwork and task routing, and keeps an audit-ready compliance record so you are never caught unprepared.

## Who this is for

This template is built for agricultural producers, growers, agribusiness operators, and farm managers who deal with multi-credential compliance across state and federal agencies. It fits operations of any size - from single-commodity row crop farms to diversified produce operations and large agribusiness enterprises - where tracking renewal deadlines manually across spreadsheets or calendar reminders has become unreliable or unscalable. It is especially valuable for operations subject to food safety audits (FSMA, GAP/GHP), chemical use licensing, or water use permitting across multiple parcels or jurisdictions.

## What it does

1. **Compliance Inventory Management** - Pulls credential records from your farm management software and ERP, cross-references status against USDA and state agriculture department portals, and maintains a single master register of every license, permit, and certification with current status and expiration date.

2. **Tiered Expiration Alerts** - Monitors all active credentials and sends staged renewal nudges at 120, 60, 30, and 14 days before expiration, with escalating urgency and recipients. Post-expiration, it surfaces emergency renewal guidance and variance options.

3. **Renewal Workflow Coordination** - Generates task lists for each renewal (forms, fees, continuing education, supporting documents), links to the correct USDA portal or state agriculture department portal for current applications, and routes tasks to the right team members through your ERP's workflow module.

4. **Document Management and Audit Readiness** - Stores renewed credentials in your document vault, maintains a version-controlled compliance register, and generates on-demand audit summaries formatted for regulators, buyers, lenders, or insurers.

5. **Compliance Reporting** - Delivers a weekly status report covering credentials due in the next 30, 60, and 90 days, renewals in progress, and completed renewals - with cost tracking and gap analysis as your operation's activities or workforce change.

## Key integrations

- **Farm management software (e.g., Granular, AgriWebb, Trimble Ag, FarmLogs)** - Source of operator records, equipment lists, parcel data, and document storage for credentialing tied to specific people and assets.
- **ERP (e.g., SAP, Microsoft Dynamics 365, AgriForce)** - Task routing and workflow management for renewal action items; source of organizational structure and role assignments.
- **USDA portals (AMS, APHIS, eAuthentication)** - Authoritative source for organic certification status, GAP/GHP audit scheduling, and federal permit applications and fee schedules.
- **State agriculture department portals** - Renewal forms, status checks, and deadline information for pesticide applicator licenses, water use permits, and state-specific food safety credentials.

## Getting started

1. **Import this workspace** into Gamut using the workspace-zip import flow. The agent and its onboarding skill will be ready immediately.
2. **Run the `agent-onboarding` skill** - type `/agent-onboarding` in the agent chat. The skill will walk you through a short setup interview covering your operation's credential inventory, connected systems, team structure, and alert preferences.
3. **Give your first task** - once onboarding is complete, try: "Show me everything expiring in the next 90 days" or "Start a renewal checklist for our pesticide applicator licenses."

## Configuration

Onboarding writes a `config.json` file at the workspace root with your operation's system connections, credential categories, alert recipients, and escalation contacts. It also fills in the `## Your context` section at the bottom of `CLAUDE.md` with a plain-English summary of your setup. You can edit either file directly at any time to update your configuration.

---

Relevant subsegments: AGRI
