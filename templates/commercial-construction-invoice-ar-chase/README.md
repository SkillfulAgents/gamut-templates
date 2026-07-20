> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/invoice-ar-chase/commercial-construction-invoice-ar-chase)** — one-click deploy, no setup.

# Commercial Construction/GC - Invoice & AR Chase

Construction AR doesn't collect itself. Pay applications sit in owners' approval queues, retainage languishes past substantial completion, and invoices age while PMs focus on the job. This Gamut agent monitors every open receivable, sends professionally-worded follow-ups at the right time and tone, escalates toward lien rights when needed, and delivers a weekly cash and AR digest so the controller always knows what's outstanding and what's been done about it.

## Who this is for

General contractors, construction managers, and specialty contractors who bill on AIA G702/G703 pay applications or standard invoices and need a systematic way to follow up on slow-paying owners and clients without burning relationships or leaving money on the table.

## What it does

1. **Monitors all open receivables daily** - pulls pay applications, standard invoices, and retainage balances from Sage 300 CRE, Viewpoint Vista, or Procore Financials and organizes them by aging bucket
2. **Checks payment window before reaching out** - verifies that each item is past its contractual payment deadline before sending a follow-up, so the agent never chases early
3. **Sends tiered, owner-voiced follow-ups** - first reminder at 1-30 days (friendly, confirm receipt), second at 31-60 (direct, payment date requested), formal notice at 61-90 (contract terms cited), pre-lien notice staged at 90+ for principal review
4. **Tracks retainage and release triggers** - maintains a separate retainage ledger and alerts the PM when substantial completion or other release triggers are approaching so retainage doesn't sit past its due date
5. **Logs every action and response** - records sent messages, payment receipts, disputes, and payment arrangements in the AR tracker for full audit trail
6. **Delivers the weekly cash and AR digest** - Monday morning summary with total open AR, aging breakdown, top overdue items, last week's collections, and items requiring principal input
7. **Escalates appropriately** - stages Tier 3 and Tier 4 notices for principal review; never sends lien-rights language without authorization

## Key integrations

- **Sage 300 CRE** - primary source for invoices, pay application status, and AR aging
- **Viewpoint Vista** - alternative accounting source for pay app status, project billing, and AR data
- **Procore** - source for pay application workflow status, project correspondence, and contractor payment tracking
- **Email** - primary channel for all follow-up messages; BCC to PM and controller on escalated tiers

## Getting started

1. **Import this workspace** into Gamut using the workspace-zip import flow.
2. **Run the `agent-onboarding` skill** - the agent will ask about your billing systems, invoice formats, payment terms, and who should receive the weekly digest. Lien rights state coverage is confirmed during onboarding.
3. **Give it your first task** - a good first prompt: "Pull our open AR from Sage and show me everything more than 30 days overdue with a recommended follow-up action for each."

---

Relevant subsegments: GCON
