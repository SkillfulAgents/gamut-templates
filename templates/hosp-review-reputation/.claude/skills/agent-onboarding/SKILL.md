---
name: agent-onboarding
---

# Agent Onboarding

Welcome — let's configure your Hospitality/Hotels Review and Reputation Replies agent. I'll ask about your property, connected review platforms, PMS, escalation contacts, and delivery preferences. About 8 minutes.

---

## Property basics

1. What is your property's name, type (independent hotel, boutique, select-service brand, resort), and primary guest segments (leisure, corporate, groups, events)?
2. Who is the General Manager or guest relations contact whose name should appear on replies?

---

## Review platforms

3. Which review platforms should the agent monitor — Google Business Profile, TripAdvisor, Yelp, Booking.com, Expedia, or others? Which are highest priority for your property?
4. Do you want the agent to post replies directly (auto-post after review) or draft replies for your approval before posting?

---

## PMS connection

5. Do you use Opera, Cloudbeds, or another PMS? Should the agent cross-reference reviewer names and stay dates against reservation records to identify room types and stay segments?

---

## Escalation

6. Who should receive escalation alerts for 1-2 star reviews mentioning cleanliness, safety, billing, or unresolved complaints — the GM, duty manager, or a specific email/Slack handle?
7. What is the fastest way to reach that person for urgent escalations (email, Slack, or front desk system message)?

---

## Tone and voice

8. How should replies be signed — General Manager's name, "The [Property Name] Team", or something else?
9. Are there any topics that should never appear in a public reply (e.g., staff names, pricing details, internal policies)?

---

## Digest delivery

10. Who should receive the weekly rating trend digest, and in what format — Slack, email, or both?

---

## After Questions Are Answered

1. **Update CLAUDE.md** with: property name, property type, guest segments, GM name and reply sign-off, connected review platforms, auto-post setting, PMS connection, escalation contact and channel, reply tone notes, and digest recipient.

2. **Create config.json** at `.claude/skills/agent-onboarding/config.json`:

```json
{
  "property_name": "",
  "property_type": "hotel | boutique | select-service | resort | other",
  "guest_segments": [],
  "gm_name": "",
  "reply_sign_off": "",
  "review_platforms": [],
  "auto_post_replies": false,
  "pms": "opera | cloudbeds | other | none",
  "pms_connected": false,
  "escalation_contact": "",
  "escalation_channel": "slack | email | front-desk",
  "reply_tone_notes": "",
  "digest_recipients": [],
  "digest_day": "monday",
  "digest_channel": "slack | email | both"
}
```

3. **Give the user their first task prompt.** Suggest:

   > "Pull this week's new reviews and draft replies."

   or

   > "Check for any unanswered reviews from the last 48 hours and prioritize by urgency."
