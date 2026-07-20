> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/bid-proposal-drafter/commercial-construction-bid-proposal-drafter)** — one-click deploy, no setup.

# Commercial Construction / GC - Bid Proposal Drafter

Turn an inbound RFP or bid invite into a structured first-pass proposal - pulling past project references, sub-contact lists, and standard scope templates from Procore and Sage - with a prioritized missing-information checklist for the estimator.

---

## The problem it solves

Estimators at commercial GCs spend hours on each bid assembling the same information: digging through past projects for references, re-typing standard scope language, chasing down sub contacts, and rebuilding the proposal structure from a blank document. The result is inconsistent quality and late submissions when bid volume spikes.

This agent handles the assembly work so estimators can focus on pricing, scope review, and relationship calls.

---

## What it does

1. **Parses RFPs and bid invites** - Extracts all critical fields (owner, scope, due date, submission format, bonding requirements, addenda list) and flags ambiguities immediately.
2. **Pulls matching past project references** - Searches Procore for similar past projects by type, size, and market, then formats them as a ready-to-insert reference table.
3. **Assembles subcontractor contact lists by trade** - Pulls the company's approved sub list from Procore or BuildingConnected and flags any trades with thin coverage before scope packages go out.
4. **Drafts all standard proposal sections** - Executive summary, scope of work with inclusions and exclusions, proposed schedule, project team bios, and references - using the company's own templates as the base.
5. **Pulls cost benchmarks from Sage 300 CRE** - Retrieves historical cost-per-square-foot and general conditions data from past jobs for use as directional pricing benchmarks.
6. **Produces a prioritized missing-information checklist** - Every gap is categorized as bid-blocking, pricing-critical, or proposal quality so the estimator knows what to resolve first.
7. **Supports bid day closeout** - Helps compile the final bid form, verify math on totals, and confirm all required attachments are in order before submission.
8. **Tracks addenda and scope changes** - Re-parses updates as they arrive and flags any changes that affect scope coverage or pricing.

---

## Key integrations

- **Procore** - Source for past project references, subcontractor contact database, and proposal template documents library.
- **Sage 300 CRE** - Source for job cost history, cost-per-square-foot benchmarks by project type, and general conditions cost data.
- **Viewpoint Vista** - Alternative or supplemental source for job cost history and subcontractor records if Sage is not in use.
- **BuildingConnected** - Receives bid invites, tracks ITB lists, and surfaces the sub contact database for trades covered on the platform.

---

## Getting started

1. **Import this workspace** into Gamut using the workspace-zip import flow.
2. **Run the `agent-onboarding` skill** - type `/agent-onboarding` to configure your company's connected systems, self-perform trades, proposal templates, key personnel, and credentials. This takes about five minutes and only needs to be done once.
3. **Paste or upload your first RFP** - drop in the RFP document, ITB email, or BuildingConnected invite and the agent will begin parsing and drafting immediately.

---

## Who this is for

Estimators, preconstruction managers, and project managers at commercial general contractors who bid ground-up construction, renovation, and tenant improvement projects. Works for both open-shop and union GCs across market segments (office, retail, healthcare, industrial, multifamily).

---

Relevant subsegments: GCON
