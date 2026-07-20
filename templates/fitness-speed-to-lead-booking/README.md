> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/speed-to-lead/fitness-speed-to-lead-booking)** — one-click deploy, no setup.

# Fitness/Wellness/Salon/Spa — Speed-to-Lead & Booking

The first studio or spa to respond wins the client. This Gamut agent replies to every inbound lead within minutes in your voice, qualifies their interest and availability, and books the first appointment or trial class directly against your live Mindbody or Boulevard calendar — so you're converting leads while you're teaching class, with clients, or off the floor entirely.

## Who this is for

Any fitness studio, yoga or pilates center, cycling or barre franchise, wellness clinic, salon, or spa that gets inbound leads from a website, ClassPass, Mindbody Marketplace, social media, or email — and wants every one of them followed up instantly and converted without manual effort.

**Relevant subsegments: FITN**

## What it does

1. Monitors every configured lead channel: web forms, email, ClassPass and Mindbody Marketplace inquiries, social DM relays, and other integrated lead sources
2. Fires a warm, personal-feeling first-touch reply within 5 minutes of every new lead — in the owner's voice, referencing their specific interest and your current intro offer
3. Qualifies the lead conversationally across 1-2 message exchanges: service interest, experience level, availability, and motivation
4. Queries the live Mindbody or Boulevard calendar and proposes 2-3 specific upcoming slots that match what the lead told you
5. Creates the booking in the system the moment the lead confirms, applies intro offer pricing, and sends a full confirmation with prep instructions
6. Sends one follow-up nudge after 24 hours of silence, then marks the lead cold if still unresponsive — no over-messaging
7. Logs every lead, response time, conversation summary, and outcome for conversion tracking
8. Delivers a weekly lead-to-booking summary with source breakdown, conversion rate, response time averages, and intro offer redemption

## Key integrations

- **Mindbody** — live class/appointment calendar, booking creation, new client intake
- **Boulevard** — live appointment calendar, booking creation, new client intake
- **Email** — lead monitoring and outreach
- **Web form** — embedded contact or intro offer forms on your website
- **ClassPass / Mindbody Marketplace** — marketplace inquiry monitoring
- **Social DM relay** — Instagram DMs, Facebook Messenger (via configured relay or integration)

## Getting started

1. **Import this workspace** into your Gamut environment
2. **Run the `agent-onboarding` skill** — the agent will ask you about your lead channels, booking system, intro offer, brand voice, and follow-up preferences to get fully configured
3. **First task example:** "A new lead just came in from our website form — her name is Sarah, she's interested in the reformer pilates classes. Pull up the schedule and let's get her booked."

## Configuration

The agent stores your settings in two places after onboarding:

- **`config.json`** — scheduling system credentials, lead channel integrations, follow-up timing windows, and intro offer details
- **`## Your context` in CLAUDE.md** — filled in during onboarding with your studio's voice and tone guidelines, class/service menu, intro offer terms, location details, and booking policies

You can update either at any time by running the `agent-onboarding` skill again or editing directly.

## Pattern

**Horizontal pattern:** Lead Response & Router — **Wave 4 vertical skin** for Fitness / Wellness / Salon / Spa (FITN)
