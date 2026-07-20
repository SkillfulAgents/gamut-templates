> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/quote-estimate-follow-up/mfgr-quote-estimate-followup)** — one-click deploy, no setup.

# Manufacturing - Quote / Estimate Follow-up

Manufacturers send dozens of RFQ responses every week and lose booked revenue simply because no one followed up. This Gamut agent monitors every open quotation in Epicor or SAP Business One, sends estimator-voiced follow-ups that reference the specific quote number and part numbers, flags expiring proposals and tooling cost recovery at risk, and delivers a weekly win-rate report so the sales and estimating team knows exactly where the pipeline stands.

---

## Who this is for

Job shops, contract manufacturers, and industrial manufacturers who send RFQ responses regularly and want a systematic way to follow up on open quotes without the estimator manually tracking every open bid.

- Contract manufacturers and job shops sending 10 to 200+ quotes per month
- Tier 1 and Tier 2 suppliers responding to OEM RFQ cycles
- Estimating teams managing high-volume quoting without dedicated sales support
- Sales managers who want win-rate visibility without building manual reports

**Relevant subsegments: MFGR**

---

## What it does

1. Pulls all open quotations from Epicor or SAP B1, organizes them by status (awaiting response, in evaluation, follow-up attempted, expiring soon, expired), and flags any quote past its configured follow-up window.
2. Handles manufacturing-specific quote dynamics: flags tooling cost at risk on open quotes (tooling investment is not recoverable on a loss), monitors annual program price validity periods, tracks multi-revision quotes to confirm the current revision is in active follow-up.
3. Prioritizes outreach: tooling cost at risk first, then expiring quotes, then by value and days since last contact.
4. Drafts follow-up messages in the estimator's or owner's voice, referencing the specific quote number, part numbers, and send date - escalating in tone from a check-in to an expiration notice.
5. Presents all drafts for approval before sending anything to a customer.
6. Delivers a weekly win-rate report with quotes sent vs. won/lost, win rate by customer and part family, average days to decision, open pipeline value, and tooling cost at risk.

---

## What you need to set up

- Epicor or SAP Business One connected to this Gamut workspace (or ability to export open quote data as CSV)
- Customer and buyer contact list with email addresses
- Quote expiration policy (how long is a quote valid - 30 days, 60 days, 90 days?)
- Follow-up schedule preference (first follow-up after X days, second after Y days, etc.)
- Estimator or owner voice and tone preferences for outreach messages
- Slack or email channel where follow-up drafts and win-rate reports should be delivered

---

## What it does not do

- Auto-send follow-up messages (all drafts require approval)
- Modify quote prices or terms in the ERP
- Run capacity checks before accepting a large-volume win
- Recover tooling costs if a quote is lost
