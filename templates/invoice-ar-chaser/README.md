> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/invoice-ar-chase/invoice-ar-chaser)** — one-click deploy, no setup.

# Invoice & AR Chaser

> Chases unpaid invoices in your voice, escalates aging receivables by bucket, and posts a weekly cash and AR digest.

## What it does

Invoice & AR Chaser runs every weekday morning, reads your open invoices straight from your accounting platform, and ages them into buckets (current, 1-30, 31-60, 61-90, 90+). For every customer who is past due, it sends a single consolidated reminder written in your voice - not a generic bot tone - with the full list of overdue invoices and a payment link so paying is one click. As accounts get older it escalates the worst offenders to whoever owns collections, and once a week it posts you a cash and AR digest so you always know exactly what you are owed and what is at risk.

It is the outbound-money sibling of a document chaser: instead of paperwork, it chases the cash. Works for home and field services (HVAC, pest control, landscaping, cleaning, painting, alarm), trades and subcontractors, agencies, accounting firms, wholesale and distribution, manufacturing, consulting, and any other small business carrying receivables.

## What you'll need

- **Accounts:**
  - Accounting platform: QuickBooks Online, Xero, or FreshBooks
  - Tracker: Airtable, Notion, Google Sheets, or similar
  - Email: Gmail or Outlook
  - Slack (for the weekly digest and escalation alerts)
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** 2-3 real payment-reminder emails from your sent folder (these are what make the reminders sound like you, not a bot), plus your payment link or accepted payment methods

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - What you do and who you invoice (so reminders sound right for your business)
   - Which accounting platform, tracker, email provider, and Slack channel to use
   - Your preferred dunning cadence (gentle / standard / aggressive) and which aging bucket should trigger escalation
   - Who owns escalations and the balance or days-past-due threshold that should hand an account to them
   - The payment link or methods to include in every reminder
   - 2-3 actual payment-reminder emails from your sent folder so the agent matches your voice exactly
3. Once setup finishes, give the agent its first task: *"Read my open invoices and tracker but do NOT send any reminders and do NOT update any rows. Show me what you'd do today - which customers would get a reminder, what each one owes, and which accounts you'd escalate."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` - the agent's instructions and your configuration (written by onboarding).
- `.claude/skills/agent-onboarding/` - first-run setup interview.

## Notes

- Nothing auto-sends until you've confirmed the first dry-run looks correct.
- Reminders are sent as individual emails from your connected email account - the agent does not send from a shared or Gamut-owned address.
- Your accounting platform is always the source of truth for payment status. The agent re-checks it before every send, so it never chases an invoice that was already paid.
- The agent consolidates every overdue invoice per customer into one reminder - no one gets a separate email for each invoice.
- If a customer says they already paid, asks for a payment plan, or disputes an invoice, the agent flags it for you and pauses reminders. It never confirms payment, agrees to a plan, or settles a dispute on its own.
- Slack is recommended but optional; if not connected, the digest and escalation alerts will surface in email only.
- Money conversations are sensitive - the agent mirrors the tone and formality of the voice samples you give it rather than imposing its own.

Relevant subsegments: HVAC, PEST, RSTR, LAND, CLEN, PNTG, ALRM, SUBC, GCON, MKTG, PRCM, ACCT, WHSL, MFGR, MGMT, AEC, LGST, AGRI
