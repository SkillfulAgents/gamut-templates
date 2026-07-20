# Commercial Construction/GC - License / Permit / Cert Renewals

A lapsed contractor license or a sub's expired COI can stop work on a project and trigger a bond or insurance claim. Commercial GCs manage dozens of expiring items across their own licenses, their sub network's certificates of insurance, OSHA cards, bonding, and project permits — and those items are scattered across Procore, email, and shared drives. This agent consolidates all of them into a single tracker, sends timely renewal nudges to the right people, and flags lapses the same day they occur before they become a job-site problem.

## Who this is for

Project managers, compliance managers, and operations leads at commercial general contractors or construction management firms who need to keep their own licenses and their subcontractor COI/cert portfolio current without manually chasing every renewal.

Relevant subsegments: GCON

Best fit for GCs with 10+ active subcontractors and active projects in multiple jurisdictions, using Procore or Sage/Viewpoint.

## What it does

1. **Compliance tracker read** — every weekday pulls all active items (GC licenses, sub COIs, OSHA certs, bonding, project permits) from Procore, Sage/Viewpoint, or a spreadsheet register and computes days to expiry
2. **Lead-time classification** — classifies each item into renewal tiers (90/60/30/14 days) and flags lapses immediately
3. **Owner nudges** — sends one consolidated email per owner per day listing all their due items with expiry dates, document links, and specific sub COI instructions (send updated cert with GC as additional insured)
4. **Lapse escalation** — for any lapsed item, sends a same-day alert to the compliance lead and the project manager for any active project that sub is on
5. **Daily compliance digest** — posts a structured Slack summary each day: lapsed items, items due in each tier, renewals submitted, and items missing expiry dates

## Key integrations

- **Procore** — project documents, subcontractor records, permit tracking
- **Sage / Viewpoint** — subcontractor management, compliance certificates
- **Google Drive / SharePoint** — document storage for COIs, licenses, and certs
- **Slack** — daily compliance digest, lapse alerts, project manager notifications
- **Email** — renewal nudges to owners and subcontractors

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your company, systems, item types to track, lead times, and escalation preferences
3. Give the agent its first task: *"Run today's compliance check and post the digest."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`. Update either file to change lead times, nudge cadence, item types, or escalation contacts.

## Pattern

Vertical / NON-TECH - Commercial construction and general contractors

Relevant subsegments: GCON
