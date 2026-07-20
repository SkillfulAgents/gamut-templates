> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/job-project-status/mfgr-job-project-status)** — one-click deploy, no setup.

# Manufacturing - Job / Project Status

Know which jobs are in trouble before the shift starts. This Gamut agent connects to Epicor or SAP Business One, scans every open production job each morning, and delivers a daily ops brief that surfaces jobs at risk - behind schedule, missing materials, stuck at an outside processor, on a quality hold, or stalled with no recorded movement - so production management can intervene before a small problem becomes a late shipment or a premium freight bill.

---

## Who this is for

Manufacturing companies running multiple open jobs simultaneously that need a systematic way to catch production risks early - without the production manager or scheduler having to manually dig through the ERP every morning.

- Job shops and contract manufacturers managing 20 to 500+ concurrent work orders
- Tier 1 and Tier 2 automotive and industrial suppliers with strict customer ship-date commitments
- Plant managers and production schedulers who currently rely on a morning walk-through or spreadsheet to find problems
- Operations teams using Epicor or SAP Business One as the system of record for production

**Relevant subsegments: MFGR**

---

## What it does

1. Pulls all open production jobs or work orders from Epicor or SAP B1 each morning and provides a summary count (total open, on track, at risk, critical) before diving into the risk list.
2. Classifies flagged jobs into five risk categories: behind schedule, material shortage (with the specific missing part flagged), outside process delay (with processor name and overdue days), quality hold (NCR, FAI hold, or customer inspection), and stalled (no recorded movement for 3+ days).
3. Ranks flagged jobs by urgency - customer ship date within 5 days first, then by SLA penalty risk, then by days overdue.
4. Delivers a concise daily ops brief with a summary line, critical jobs (ship date within 3 days and at risk), at-risk jobs, and yesterday's resolved items.
5. Tracks recurring risk patterns over time - specific outside processors that consistently delay, bottleneck work centers, chronic material shortages - and surfaces them in a weekly plant manager summary.

---

## What you need to set up

- Epicor or SAP Business One connected to this Gamut workspace (read access to work orders, routings, inventory, and NCR status)
- Configured shop schedule and work order due dates in the ERP
- Outside processor list (company name, lead time standard, contact)
- Customer SLA or penalty terms flagged in the ERP (if applicable)
- Slack or email channel where the daily ops brief and weekly pattern summary should be delivered

---

## What it does not do

- Change production schedules or work order priorities in the ERP
- Communicate directly with customers about late shipments
- Replace the production manager's judgment on how to resolve a flagged risk
