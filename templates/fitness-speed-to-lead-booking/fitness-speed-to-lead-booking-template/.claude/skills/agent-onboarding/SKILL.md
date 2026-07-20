---
name: agent-onboarding
---

# Agent Onboarding

Welcome — let's get your Speed-to-Lead & Booking agent configured in about 2 minutes. I'll ask a few questions so the agent knows your business, where your leads come from, how your calendar works, and how you want leads handled. Answer as briefly or fully as you like; you can always update settings later.

---

## Business basics

1. What is your business name and type? (For example: Radiant Yoga Studio, yoga/pilates; The Blowout Bar, hair salon; Peak Performance Gym, personal training gym)
2. What city are you in, and what is your timezone?

---

## Lead channels

3. Where do your inbound leads come from today? Check all that apply: web contact form, email inquiry, ClassPass, Mindbody Marketplace, Instagram DMs, other social DMs, phone voicemail forwarded to email, or something else?
4. Which of these channels is already connected to Gamut, or is there a specific inbox or form-notification email address we can watch for new leads?

---

## Booking system

5. Do you use Mindbody or Boulevard for scheduling — or another system?
6. Is your booking system connected to Gamut so the agent can check live availability and confirm bookings? If not, we can note it as a manual step for now.
7. What is the first appointment or class type you want new leads to book? For example: intro offer, trial class, free consultation, 50% off first service.

---

## Brand voice and messaging

8. How would you describe your brand voice — warm and personal, high-energy and motivating, calm and professional, something else?
9. Do you have a current intro offer (for example, "first class free" or "50% off your first facial") that the agent should mention in every first-touch reply?
10. Is there anything the agent should avoid saying in outbound messages — specific words, competitors, pricing topics, etc.?

---

## Follow-up preferences

11. How long should the agent wait before sending a follow-up nudge if a lead goes quiet after the first reply? (Default is 24 hours — adjust if you prefer sooner or later.)
12. After one follow-up with no reply, should the agent mark the lead as cold and stop, or escalate it to you for a personal touch?

---

## Tracking and reporting

13. Where should the lead log go — a Google Sheet (share the URL or we can create one), your CRM, or just in the agent session for now?
14. Who should receive the weekly lead-to-booking summary, and how — email, Slack message, or in-chat?

---

## After Questions Are Answered

Once the user has answered all questions above, do the following:

1. **Write configuration to CLAUDE.md.** Fill in the `## Your context` section at the bottom of `CLAUDE.md` with a clean summary of the answers, using this structure:

```
## Your context

**Business name:** [name]
**Business type:** [type]
**City / Timezone:** [city, timezone]

**Lead channels:** [list of active channels]
**Monitored inbox or form email:** [address or "not yet connected"]

**Booking system:** [Mindbody / Boulevard / other]
**Booking system connected:** [yes / no / manual for now]
**First booking target:** [intro offer name or class type]

**Brand voice:** [description]
**Intro offer:** [offer text, or "none"]
**Messaging avoid list:** [items, or "none"]

**Follow-up wait window:** [hours]
**Post-follow-up action:** [mark cold / escalate to owner]

**Lead tracking destination:** [Google Sheet URL / CRM name / session only]
**Weekly summary recipient:** [name and channel]
```

2. **Create `config.json`** in the workspace root with the same values in machine-readable form:

```json
{
  "businessName": "",
  "businessType": "",
  "timezone": "",
  "leadChannels": [],
  "monitoredInbox": "",
  "bookingSystem": "",
  "bookingSystemConnected": false,
  "firstBookingTarget": "",
  "brandVoice": "",
  "introOffer": "",
  "messagingAvoidList": [],
  "followUpWaitHours": 24,
  "postFollowUpAction": "mark_cold",
  "leadTrackingDestination": "",
  "weeklySummaryRecipient": "",
  "weeklySummaryChannel": ""
}
```

3. **Give the user their first example prompt** — something like:

"You're all set. Here's a prompt to get started:

*'Show me all new leads from the past 24 hours and draft first-touch replies for any that haven't been contacted yet.'*

Or if you want to test the flow: *'Simulate a new lead named Alex who found us on Instagram and is interested in a trial yoga class — draft my first-touch reply.'*"
