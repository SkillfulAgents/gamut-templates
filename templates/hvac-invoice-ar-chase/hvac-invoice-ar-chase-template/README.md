# HVAC/Plumbing/Electrical — Invoice & AR Chase

Stop leaving money in open AR because no one had time to make the call. This agent watches your unpaid invoices in ServiceTitan or FieldEdge, tiers them by aging, drafts follow-up messages in your voice, and delivers a weekly AR digest — all without adding a single hour to your office staff's week.

## Who this is for

Trade contractors — HVAC, plumbing, electrical, or combined — whose AR lives in ServiceTitan or FieldEdge and whose office team is spending too many hours manually chasing residential and commercial customers on past-due invoices.

A residential HVAC company closing 15–25 jobs per week can carry $40–80K in open AR at any time. A significant chunk of that sits uncollected simply because no one followed up. This agent closes that gap.

**Relevant subsegments: HVAC**

Ideal fit:
- Owner-operated or small-team contractors (2–20 office/field staff)
- Companies with a mix of residential and commercial accounts
- Shops where the office manager is already stretched thin
- Businesses that have tried spreadsheet-based AR tracking and fallen behind

## What it does

1. **Pulls open invoices daily** from ServiceTitan or FieldEdge and classifies every unpaid invoice by aging tier: current (0–30 days), 30–60 days, 60–90 days, 90–120 days, and 120+ days.
2. **Drafts follow-up messages in your voice** — cordial for early-stage reminders, firmer as accounts age, and escalated for 90+ day accounts — at the reminder thresholds you configure.
3. **Queues every draft for your approval** before anything is sent; you or your office manager reviews and approves, edits, or skips each message.
4. **Flags commercial accounts separately** so they get the right contact, format, and tone — commercial AP departments often need a different approach than residential customers.
5. **Logs every outreach attempt** — date, message, customer response, and any payment received — so you always have a full collection history per invoice.
6. **Escalates 90+ day accounts** to you directly with a summary of prior attempts and a recommended next action: collection agency referral, lien notice, or service hold.
7. **Delivers a weekly cash and AR digest** showing total open AR by tier, week-over-week change, invoices paid, and any accounts flagged for escalation.

## Key integrations

- **ServiceTitan** — open invoice and customer data
- **FieldEdge** — open invoice and customer data (alternative platform)
- **Email** — customer outreach channel
- **Slack or Email** — approval queue and weekly AR digest for the owner or office manager

## Getting started

1. **Import this workspace** into Gamut using the workspace import flow.
2. **Run the `agent-onboarding` skill** — the agent will ask you a short set of questions about your platform, AR thresholds, escalation rules, and preferred voice, then save your configuration automatically.
3. **Send your first prompt** — for example: "Pull today's open invoices and show me everything past 30 days" — and the agent will classify your AR and draft the first round of reminders for your review.

## Configuration

All configuration is captured during onboarding and saved to `CLAUDE.md`. Key settings include:

- **Field service platform:** ServiceTitan, FieldEdge, or manual AR export
- **Trade and customer mix:** residential, commercial, or both
- **Reminder threshold:** when first reminders go out (7, 14, or 30 days past due)
- **Owner voice:** professional/polite, firm/direct, or a blend
- **Residential vs. commercial tone:** same or differentiated
- **Escalation threshold:** the aging tier at which the agent escalates instead of drafting another reminder
- **Escalation action:** collection referral, lien notice, or flag for review
- **Excluded accounts:** service contracts or commercial relationships that should never receive automated outreach
- **Approver:** owner or office manager
- **Digest and approval delivery:** email or Slack

## Pattern

Vertical / NON-TECH — HVAC, plumbing & electrical accounts receivable
