> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/license-permit-renewals/hvac-license-permit-renewals)** — one-click deploy, no setup.

# HVAC/Plumbing/Electrical — License / Permit / Cert Renewals

One lapsed EPA 608 card. One tech on a refrigerant call. One failed inspection, a voided permit, and a very unhappy homeowner. Trade contractors carry a dense stack of credentials — state licenses, NATE certs, insurance COIs, municipal permits, vehicle registrations — across every tech and every entity. Tracking them in a spreadsheet that nobody updates is how things slip. This agent keeps the whole stack current, sends tiered renewal nudges well before anything lapses, and surfaces job-assignment conflicts before they become problems.

---

## Who this is for

Trade contractors who need to stay ahead of credential renewals across their workforce and business entities — without relying on a spreadsheet that only gets opened after something expires.

- HVAC service and installation companies
- Plumbing contractors
- Electrical contractors
- Multi-trade shops (HVAC + plumbing, HVAC + electrical)
- Service businesses with 2–100+ field technicians

**Relevant subsegments: HVAC**

---

## What it does

1. Maintains a structured credential registry for every technician and business entity — state contractor licenses, EPA Section 608 refrigerant cards, NATE certifications, journeyman and master licenses, liability and workers' comp COIs, vehicle registrations, and municipal trade permits.
2. Monitors expiry dates daily and sends tiered renewal reminders at 90, 60, 30, and 14 days out — with escalating urgency and direct links to renewal portals where available.
3. Immediately alerts the owner and flags the tech as non-deployable on credential-required jobs if a credential lapses without a recorded renewal.
4. Logs renewal actions — submission date, receipt date, new cert number — so the registry stays accurate and auditable at all times.
5. Cross-references lapsed or at-risk credentials against upcoming ServiceTitan or FieldEdge job assignments and surfaces conflicts (e.g., tech with lapsed EPA 608 assigned to a refrigerant recovery job).
6. Generates audit-ready compliance summaries on demand — scoped to the full roster, a single tech, or a specific credential type — formatted for sharing with clients, insurers, or internal review.

---

## Key integrations

- **ServiceTitan** — job assignment cross-reference for credential conflict detection
- **FieldEdge** — job assignment cross-reference for credential conflict detection
- **Email / Slack / SMS** — reminder delivery channel (configured during onboarding)
- **State licensing portals** — linked in reminders for direct renewal navigation (added manually or via onboarding)

---

## Getting started

1. **Import this workspace** into Gamut using the workspace zip import flow.
2. **Run the `agent-onboarding` skill** — the agent will walk you through your trade type, states of operation, tech roster, and credential inventory before it starts tracking anything.
3. **First task example:** "Add EPA 608 Universal cert for Marcus Rivera, cert number E608-77421, expires 2027-03-15" — or paste in a spreadsheet export and ask the agent to load it.

---

## Configuration

The following are set during onboarding and stored in `config.json`:

| Setting | Description |
|---|---|
| `trade` | Primary trade (HVAC, plumbing, electrical, multi-trade) |
| `states` | States of operation (for license tracking) |
| `techs` | Tech roster with names and roles |
| `reminder_windows_days` | Reminder thresholds (default: 90, 60, 30, 14) |
| `escalation_contact` | Owner/manager notified on lapses and 14-day alerts |
| `reminder_channel` | Delivery method: email, Slack, SMS |
| `field_software` | ServiceTitan, FieldEdge, or none |
| `job_conflict_check` | Whether to cross-reference assignments on alerts |

---

## Pattern

Vertical skin — Compliance / Renewal Tracker (Wave 4), specific to HVAC/plumbing/electrical trade licensing, EPA 608, NATE, and contractor credentialing requirements.
