> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/license-permit-renewals/restaurant-qsr-license-permit-renewals)** — one-click deploy, no setup.

# Restaurant/QSR - License / Permit / Cert Renewals

Restaurants and QSRs operate under a dense web of regulatory credentials - food handler cards, health department operating permits, liquor licenses, fire safety certificates, and more. Each has its own renewal timeline, issuing authority, and consequences for lapsing. This agent keeps every credential in one registry, sends tiered renewal alerts at 90/60/30/7 days out, coordinates the renewal workflow with the right staff member, and produces audit-ready compliance summaries on demand, so an inspector walk-in or a franchisor audit never catches you off guard.

## Who this is for

This template is built for restaurant owners, operators, and GMs running single or multi-location food service businesses - including full-service restaurants, quick-service restaurants (QSR), fast casual, bars, and food trucks. It is especially valuable for operations with high employee turnover (where food handler card lapses are common) and for multi-unit operators managing a patchwork of jurisdictions with different permit requirements and renewal calendars.

## What it does

1. **Credential registry** - Maintains a master inventory of every license, permit, and certification across all locations, with expiration dates, issuing authorities, responsible owners, and document storage links.

2. **Tiered renewal alerts** - Monitors expiration dates daily and sends calibrated alerts at 90 days (informational), 60 days (action required), 30 days (urgent), and 7 days (critical escalation) to the right person for each credential.

3. **Renewal workflow coordination** - Generates structured renewal tasks with portal URLs, processing timelines, renewal fees, and submission tracking for each credential type - including health permits requiring inspections and state liquor board requirements.

4. **Employee certification tracking** - Cross-references active staff from Toast POS or Square against food handler card expiration dates, producing a per-location roster view of who is current, expiring soon, or lapsed.

5. **Audit-ready compliance packages** - Assembles on-demand compliance summaries formatted for internal use (full detail) or external audiences (inspectors, franchisors), flagging any credentials that are expired or missing documents.

## Key integrations

- **Toast POS** - Source of truth for the active employee roster; used to match food handler certifications against staff currently on payroll.
- **Square** - Alternative or supplemental staff and scheduling data source for operations not on Toast; used to validate certification coverage across shifts.
- **Google Business Profile / Yelp** - Monitored for public health inspection score updates or posted violations that may signal a recent inspection or compliance issue.
- **Health department portals** - Jurisdiction-specific portals for permit status lookups, inspection report retrieval, renewal submission tracking, and fee payment (configured per location during onboarding).

## Getting started

1. **Import the workspace** - In Gamut, import this zip as a new workspace. The agent and onboarding skill will be ready immediately.
2. **Run agent-onboarding** - Type `run agent-onboarding` in the workspace. The skill will walk you through your locations, credential types, key systems, and renewal contacts, then write your configuration automatically.
3. **Give your first task** - Once onboarding is complete, try: "Show me everything expiring in the next 60 days across all locations."

## Configuration

After onboarding, your settings are saved to `.claude/config.json` in the workspace. You can edit this file directly to add new locations, update portal URLs, or change renewal alert recipients. The `## Your context` section at the bottom of `CLAUDE.md` contains a plain-English summary of your setup - update it any time your configuration changes.

---

Relevant subsegments: FOOD
