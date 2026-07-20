# Fitness/Wellness/Salon/Spa — Speed-to-Lead & Booking

Stop losing leads to slow follow-up. This agent replies to every inbound inquiry within minutes in your voice, qualifies the prospect, checks your live calendar, and books the first appointment or trial class — all before your competitor picks up the phone.

## Who it is for

Fitness studios, gyms, salons, and spas that capture leads from web forms, Instagram DMs, ClassPass inquiries, or phone-to-voicemail and lose them because the first reply takes hours or never comes. If a prospective member submits a form at 2pm and doesn't hear back until 5pm, they've already booked somewhere else.

Relevant subsegments: FITN

## What it does

1. Monitors every connected inbound lead channel — web form submissions, email inquiries, ClassPass and Mindbody Marketplace messages, and social DM relays.
2. Drafts a warm, personal first-touch reply within 5 minutes in your configured brand voice, acknowledging the specific service or class they asked about.
3. Asks a short qualifier to learn what the lead is interested in and when they are generally available.
4. Checks your live Mindbody or Boulevard calendar and proposes 2 to 3 specific booking slots that match the lead's preferences.
5. Confirms the booking directly in Mindbody or Boulevard and sends a confirmation with what to bring or expect.
6. Sends a single follow-up nudge to leads that go quiet after 24 hours, then logs them as cold if still no reply.
7. Logs every lead, reply time, qualification outcome, and booking result to a tracking sheet or CRM.
8. Delivers a weekly lead-to-booking summary: total leads, replied within 5 minutes (%), booked (%), and ghosted (%).

## Key integrations

- **Mindbody** — live calendar availability, booking confirmation, Marketplace message ingestion
- **Boulevard** — live calendar availability and appointment booking for salons and spas
- **Gmail / email inbox** — web form submission forwarding and email inquiry monitoring
- **Google Sheets** — lead tracking log and weekly summary
- **Instagram DM relay** — social inquiry ingestion via connected relay or inbox forwarding
- **ClassPass** — inquiry ingestion from ClassPass Marketplace messages

## Getting started

1. **Import this workspace** into your Gamut environment.
2. **Run the agent-onboarding skill** — the agent will ask you a short set of questions to configure your business name, lead channels, booking system, brand voice, and follow-up preferences.
3. **Send your first prompt** — try: "Show me all new leads from the past 24 hours and draft first-touch replies for any that haven't been contacted yet."

## Configuration

All configuration is set during onboarding and stored in `CLAUDE.md` under `## Your context` and in `config.json`. You can re-run onboarding at any time by typing "run agent-onboarding" in the chat.

Key configuration items:
- Business name and type
- Connected lead channels
- Booking system (Mindbody or Boulevard) and connection status
- Intro offer text for first-touch replies
- Brand voice description
- Follow-up wait window (default: 24 hours)
- Lead tracking destination (Google Sheet, CRM, or session)
- Weekly summary recipient and channel

## Pattern

Vertical / NON-TECH — Fitness, wellness, salon & spa lead conversion. Wave 4.
