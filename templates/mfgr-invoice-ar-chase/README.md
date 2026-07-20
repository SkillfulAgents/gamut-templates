> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/invoice-ar-chase/mfgr-invoice-ar-chase)** — one-click deploy, no setup.

# Manufacturing - Invoice & AR Chase

Manufacturing AR is slow-pay by design. OEMs and distributors run three-way match, sit on net-60 terms, and let invoices age until someone calls their AP department with a PO number. This Gamut agent connects to Epicor or SAP Business One, tracks every open invoice against a 30/60/90/120-day ladder, distinguishes true overdue balances from three-way match process holds, drafts follow-up messages in your voice that reference the customer's PO number, and delivers a weekly cash and DSO digest - so the controller can manage AR without burning hours on manual follow-up.

---

## Who this is for

Manufacturing companies that sell B2B - to OEMs, distributors, or industrial buyers with formal AP processes - and need a systematic way to collect without straining customer relationships or losing track of which invoices are truly overdue versus stuck in a customer process hold.

- Contract manufacturers and job shops with net-30 to net-60 customer terms
- Tier 1 and Tier 2 automotive and industrial suppliers invoicing OEM AP departments
- Manufacturers managing blanket purchase orders with scheduled release invoicing
- Controllers and accounting managers overseeing 50 to 500+ open customer invoices

**Relevant subsegments: MFGR**

---

## What it does

1. Pulls all open invoices daily from Epicor or SAP B1 and classifies them by aging tier: current (0-30), 30-60, 60-90, 90-120, and 120+ days past due.
2. Handles manufacturing-specific AR complexity: flags invoices missing a customer PO number (AP hold risk), monitors blanket order cumulative invoiced totals against the blanket ceiling, distinguishes three-way match process holds from true overdue balances, and flags customers at credit limit.
3. Drafts tiered follow-up messages referencing the specific invoice number, customer PO number, and payment due date - calibrated from a friendly check-in to a final notice before collections.
4. Presents all drafts for approval before sending. The agent never auto-sends to customers.
5. Escalates 90+ day balances to the controller or owner with recommended next actions: credit hold on new orders, collections referral, or UCC lien notice.
6. Delivers a weekly cash and AR digest with open AR by tier, top balances, DSO vs. prior week, three-way match holds, short-pays, and recommended actions.

---

## What you need to set up

- Epicor or SAP Business One connected to this Gamut workspace (or ability to export AR aging report as CSV)
- Customer AP contact list (AP department email per customer)
- Credit limit thresholds by customer
- Controller or owner tone and voice preferences for outreach messages
- Slack or email where drafts and the weekly AR digest should be delivered

---

## What it does not do

- Auto-send follow-up messages (all drafts require approval)
- File UCC liens or initiate legal action
- Process payments or post cash receipts in the ERP
