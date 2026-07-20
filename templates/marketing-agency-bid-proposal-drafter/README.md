> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/bid-proposal-drafter/marketing-agency-bid-proposal-drafter)** — one-click deploy, no setup.

# Marketing/Creative Agency - Bid / Proposal Drafter

Marketing and creative agencies field RFPs and bid requests constantly, but assembling a polished first-pass proposal from scratch is a time drain that pulls account leads away from client work. This agent ingests an incoming RFP, pulls relevant past deals and pricing from HubSpot, assembles a structured draft using the agency's own templates and comparable work, and delivers a ready-to-finalize proposal alongside a missing-info checklist — so the account lead refines and sends rather than builds from a blank page.

Relevant subsegments: MKTG

## Who this is for

Account leads, agency principals, and new-business teams at marketing and creative agencies that field recurring RFPs and bids, have deal history in HubSpot they are not systematically mining, and lose hours per pitch assembling proposals manually from scratch.

Best fit for agencies running 10–100 active proposals per year across campaigns, rebrands, content, paid media, websites, or integrated retainers.

## What it does

1. **Ingest & parse the RFP** — accepts the bid in any form (pasted text, PDF, email, or direct brief); extracts scope, deliverables, timeline, and budget; and logs or updates the deal in HubSpot before drafting begins
2. **Pull relevant past work & comparable deals** — searches HubSpot closed-won history for the 2–3 most comparable engagements and surfaces original scope, pricing, team composition, and case study assets as the pricing and narrative anchor
3. **Assemble the first-pass proposal** — drafts a complete, structured proposal (executive summary, scope interpretation, approach, team, timeline, investment, why-us, next steps) using comparable deal data and the agency's configured template library
4. **Generate the missing-info checklist** — produces a structured internal checklist of every scope gap, pricing assumption, timeline risk, team assignment, and approval needed before the proposal can go to the client
5. **Create the Asana task & proposal project** — opens an Asana task in the proposals project, attaches the draft and checklist, assigns it to the account lead, adds subtasks for each open item, and flags high-value bids for principal review
6. **Update HubSpot & track proposal status** — moves the deal to the correct stage, logs proposal value and version, sets follow-up reminders, and records closed-won/lost outcomes to improve future comparable-work lookups

## Key integrations

- **HubSpot** — CRM for deal history, contact/company enrichment, deal stage management, and follow-up task creation
- **Asana** — proposal project tracking, task assignment, missing-info subtasks, and deadline management
- **Internal asset library** — configured file path or URL for boilerplate sections, team bios, case study summaries, and portfolio links

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your agency, your HubSpot and Asana setup, your standard proposal structure, and your pricing norms, then configure the agent for your business
3. Give the agent its first task: *"Here's an RFP we just received — draft a first-pass proposal and flag everything we need to confirm before sending."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`. Edit either file to update the agency name and voice, HubSpot pipeline and deal stage names, Asana project ID, proposal template structure, high-value deal threshold, follow-up window, or the path to the internal asset library.

## Pattern

Vertical / NON-TECH — Marketing & creative agency new business ops
