> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/bid-proposal-drafter/aec-bid-proposal-drafter)** — one-click deploy, no setup.

# Architecture/Engineering/Design - Bid / Proposal Drafter

Every AEC firm knows the pain: an RFP lands on a Friday afternoon, the submission deadline is in ten days, and the project manager is staring at a blank document while juggling three active projects. This agent changes that. Feed it the solicitation and it pulls relevant past project descriptions, team bios, and fee schedule templates from your existing systems - Deltek, BQE Core, Procore - assembles a structured first-pass proposal, and hands back a prioritized checklist of what still needs PM attention. You go from blank page to reviewable draft in a fraction of the time.

## Who this is for

Architecture, engineering, and design firms that respond to RFPs, RFQs, and competitive bids on a regular basis. This template is built for practices that maintain project data in Deltek Vision or Vantagepoint, BQE Core, or similar firm management systems, and that want to reduce the administrative burden on project managers and principals during the pursuit process. It works for firms of any size pursuing public agency contracts, private owner work, design-build, or consultant selection RFQs.

## What it does

1. **Parses the solicitation** - Extracts key requirements, deadlines, required sections, page limits, and evaluation criteria from any RFP or RFQ format, and flags ambiguities for early PM clarification.

2. **Retrieves relevant past projects** - Searches Deltek or BQE Core for completed projects that match the solicitation's scope, sector, and scale, then selects and ranks the best references for inclusion.

3. **Assembles team bios and org chart content** - Pulls staff profiles for the proposed team from your firm management system, formatted to the solicitation's requirements, with credential gaps flagged.

4. **Drafts the fee schedule and scope of work** - Maps solicitation scope items to your standard service phases and populates a draft fee table from your existing rate templates, with atypical items flagged for PM review.

5. **Produces a missing-information checklist** - After assembling the draft, delivers a prioritized checklist of every gap - categorized by compliance priority and sorted by urgency - so the PM knows exactly what to chase down before submission.

## Key integrations

- **Deltek Vision / Vantagepoint** - Primary source for project records (descriptions, metrics, client names, awards), staff profiles, and fee/rate data used in the proposal.
- **BQE Core** - Alternative or supplementary source for project and staff data at firms using BQE for project accounting and time tracking.
- **Procore** - Source for active project documentation, bid logs, and any project files relevant to the pursuit; also used to update bid tracking records.
- **Project management systems** - Broader category covering tools like Smartsheet, Asana, or firm-specific PM platforms used to track pursuit status and coordinate proposal tasks across the team.

## Getting started

1. **Import this workspace** into Gamut using the workspace-zip import flow.
2. **Run the `agent-onboarding` skill** - the agent will ask a short set of questions about your firm's systems, typical proposal structure, and connected data sources. Your answers are saved to `config.json` and summarized in the agent's context section.
3. **Give it your first task** - paste or attach an RFP/RFQ and ask the agent to draft a proposal. A good first prompt: "Here is an RFP we received today. Please parse it, pull relevant past projects from Deltek, and draft a first-pass proposal with a missing-information checklist."

## Configuration

After onboarding, your firm-specific settings are stored in `config.json` at the workspace root. The `## Your context` section at the bottom of `CLAUDE.md` holds a plain-English summary of your setup - firm name, connected systems, default team structure, and any standing preferences for proposal format. You can update either file directly if your systems or preferences change.

---

Relevant subsegments: AEC
