# Franchise Systems - License / Permit / Cert Renewals

Franchise networks are held responsible for every location's compliance — a lapsed health permit or an expired COI is a liability exposure for the entire brand. With dozens or hundreds of locations across multiple jurisdictions, keeping track of expiration dates manually is a full-time job. This agent tracks every location's compliance items across the network, nudges franchisee operators on a lead-time schedule, copies the franchisor compliance team when items are close to expiry, and flags lapses the same day they occur.

## Who this is for

Franchisor compliance teams and multi-unit franchisee operators who need to track business licenses, health permits, training certifications, COIs, and equipment inspections across a location network.

Relevant subsegments: FRNC

Best fit for franchise systems with 5-200 locations using a franchisor portal or ServiceTitan, managing compliance items across multiple states.

## What it does

1. **Network compliance tracker read** — every weekday pulls all active compliance items (business licenses, health permits, fire certs, brand certifications, COIs, equipment inspections) from the connected portal or spreadsheet and computes days to expiry per location
2. **Lead-time classification** — classifies items into renewal tiers (90/60/30/14 days) and immediately escalates lapses
3. **Franchisee operator nudges** — one consolidated email per operator per day listing all their location's due items; copies the franchisor compliance lead on items within 30 days
4. **Lapse escalation** — same-day alert to the operator and franchisor compliance lead for any lapsed item; flags whether the lapse is an operational risk (health permit, fire cert) vs. a fine risk (business license)
5. **Network compliance digest** — daily or weekly Slack summary of lapsed items, items in each renewal tier, and missing expiry dates across all locations

## Key integrations

- **Franchisor compliance portal / ServiceTitan** — location records, compliance documents
- **Google Drive / SharePoint** — document storage for COIs, permits, and certifications
- **Slack** — network digest and lapse alerts
- **Email** — renewal nudges to franchisee operators and compliance lead copies

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your network, item types, lead times, and escalation preferences
3. Give the agent its first task: *"Run today's compliance check and post the network digest."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`.

## Pattern

Vertical / NON-TECH - Franchise systems and multi-unit operators

Relevant subsegments: FRNC
