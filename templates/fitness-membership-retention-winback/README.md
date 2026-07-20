> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/membership-retention-win-back/fitness-membership-retention-winback)** — one-click deploy, no setup.

# Fitness/Wellness/Salon/Spa — Membership Retention & Win-back

Most membership churn is predictable — the signals are there weeks before someone cancels. This agent watches visit frequency, booking patterns, and billing status in Mindbody or Boulevard daily, catches the early drift before it becomes a formal cancellation, and triggers the right retention play automatically: a warm rebooking nudge, a proactive pause offer, or a targeted win-back sequence for members who have already lapsed. For operators managing recurring membership revenue, stopping one cancellation a week more than pays for the tool.

Built for fitness studios, wellness centers, salons, and spas that run membership or recurring service models and want to protect monthly recurring revenue without adding manual follow-up work to the front desk.

## Who this is for

This template is for studio owners, general managers, and membership directors at fitness, wellness, salon, or spa businesses running EFT memberships, monthly packages, or annual contracts. It works best when your member visit history and billing records live in Mindbody or Boulevard — the agent reads those systems to score at-risk members without manual data entry.

Relevant subsegments: FITN

## What it does

1. **Monitors member health signals daily** — visit frequency, booking behavior, last visit date, billing status, and service usage — pulling live data from Mindbody or Boulevard to build a current picture of every member.
2. **Classifies retention risk** into Green / Yellow / Red / Lapsed tiers, with scoring weighted by lifetime value, recency of engagement, membership type, and win-back history.
3. **Triggers the right retention play** for each member's specific signal — rebooking nudge, loyalty recognition, proactive pause offer, or personal outreach flag — without applying generic mass-blast messaging.
4. **Manages offer guardrails** to prevent over-messaging, avoid repeating offers within 90 days, and exclude members in billing disputes or with do-not-contact preferences.
5. **Escalates high-LTV members** at Red status and any member expressing cancellation intent to the manager for same-day personal follow-up.
6. **Logs every intervention** against the member's record in Mindbody or Boulevard and maintains a 90-day retention event log.
7. **Delivers a weekly retention and churn risk digest** every Monday with risk distribution, intervention response rates, LTV at risk, and a specific recommended focus for the coming week.

## Key integrations

- Mindbody (member records, visit history, booking data, messaging/marketing automation)
- Boulevard (member profiles, appointment history, billing, automated messaging)
- Google Sheets or equivalent (retention event log)
- Email or Slack (manager escalations and weekly digest)

## Getting started

1. Import this workspace into Gamut.
2. Run the `agent-onboarding` skill — type `run agent-onboarding`.
3. Send your first task prompt, for example: "Pull today's at-risk member list and send rebooking nudges to anyone who hasn't visited in 14+ days."

## Configuration

After onboarding, your business details and system settings are saved in `config.json` at the workspace root. Context about your studio (membership tiers, LTV thresholds, escalation contacts, offer library) lives in the `## Your context` section of `CLAUDE.md`. You can edit either file directly to update settings at any time.

## Pattern

Vertical / NON-TECH — Fitness, wellness, salon & spa membership retention
