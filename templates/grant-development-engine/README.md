> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/finance-accounting/grant-development-engine)** — one-click deploy, no setup.

# Grant & Development Engine

Nonprofit development teams spend enormous time searching for funders, tracking deadlines, writing applications from scratch, and drafting reports — work that is largely templatable but never gets templated because the team is stretched thin. This agent runs the full development cycle: prospecting for aligned funders, maintaining the grant calendar, drafting applications from the organization's own proposal library, producing impact reports against funder requirements, and keeping the donor communication cadence on schedule.

## Who this is for

Development directors, grants managers, and executive directors at nonprofits who manage a portfolio of grants and major donor relationships and want to spend more time on strategy and relationships rather than on document assembly and deadline tracking.

Relevant subsegments: NGO

Best fit for organizations with 3-50 active grants, a proposal library in Drive or SharePoint, and program data in a spreadsheet or simple database.

## What it does

1. **Funder prospecting** — searches configured grant databases (Candid, Instrumentl, GrantStation) for funders aligned to the organization's program areas and geography, scores them by alignment and fit, and delivers a prioritized prospect list with recommended next actions
2. **Deadline and pipeline tracking** — maintains the full grant calendar (LOI deadlines, application deadlines, report due dates), posts a weekly digest to Slack, and sends direct alerts for deadlines within 14 days
3. **Grant application drafting** — when an application is assigned, pulls the funder's RFP, searches the proposal library for reusable content, pulls current program data, and produces a draft with a missing-info checklist for the program and finance team
4. **Impact reports and stewardship content** — when a report is due, pulls program outcomes data, drafts the report against the funder's required format, and produces a stewardship letter for the development director
5. **Donor communication cadence** — tracks major donor touchpoints, drafts cultivation emails and update letters on schedule, and drafts gift acknowledgment letters within 24 hours of a logged donation

## Key integrations

- **Salesforce NPSP / Bloomerang / spreadsheet** — grant pipeline, funder contacts, and donor records
- **Candid (GuideStar) / Instrumentl / GrantStation** — funder prospecting and grant opportunity search
- **Google Drive / SharePoint** — proposal library, program data, output folder for drafts
- **Slack** — weekly pipeline digest, deadline alerts, draft delivery notifications
- **Email** — grant application notifications, stewardship letters, donor acknowledgments

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your organization, program areas, CRM, proposal library, and donor communication preferences
3. Give the agent its first task: *"Find new grant prospects for our [program area] work and add the top 5 to the pipeline."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`. Update either file to change program areas, grant database connections, proposal library path, or digest destinations.

## Pattern

Vertical / NON-TECH - Nonprofits and foundations

Relevant subsegments: NGO
