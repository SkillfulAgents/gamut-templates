---
name: agent-onboarding
---

# Agent Onboarding

Welcome — let's configure your Hospitality/Hotels Speed-to-Lead and Booking agent. I'll ask about your property, inquiry channels, PMS, brand voice, routing rules, and delivery preferences. About 8 minutes.

---

## Property basics

1. What is your property's name, type (independent hotel, boutique, select-service, resort), and primary guest segments (leisure, corporate, groups, events)?
2. What is your brand voice for guest communications — formal and luxe, warm and boutique, friendly and casual, or something else?

---

## Inquiry channels

3. Through which channels do booking inquiries arrive — website contact form, email inbox, Booking.com messages, Expedia messages, Google Business Profile messages, phone-to-text/SMS, or a combination?
4. Is there a specific email address or form endpoint where inquiries land? Please share the address or URL.

---

## PMS and availability

5. What PMS do you use — Opera, Cloudbeds, or another system? Should the agent check availability in real time before drafting replies?
6. Should the agent auto-confirm bookings for transient/leisure leads, or route all bookings to the reservations team for confirmation?

---

## Routing rules

7. At what group size should the agent route to the sales team instead of quoting rates (default: 5+ rooms)?
8. Who handles group sales and event/wedding inquiries? Provide names and Slack handles or email addresses.
9. Who is the reservations manager who should receive nudge alerts for unworked leads?

---

## Timing

10. What is your target first-response time during operating hours (default: 5 minutes)? What is the nudge window for unworked inquiries (default: 4 hours during hours, 12 hours for after-hours)?

---

## After Questions Are Answered

1. **Update CLAUDE.md** with: property name, property type, guest segments, brand voice, inquiry channels, email/form endpoint, PMS and auto-book setting, group routing threshold, sales and events contacts, reservations manager contact, first-response target, and nudge window.

2. **Create config.json** at `.claude/skills/agent-onboarding/config.json`:

```json
{
  "property_name": "",
  "property_type": "independent | boutique | select-service | resort | other",
  "guest_segments": [],
  "brand_voice": "formal | warm-boutique | friendly | other",
  "inquiry_channels": [],
  "inquiry_email": "",
  "pms": "opera | cloudbeds | other | none",
  "pms_availability_check": true,
  "auto_confirm_transient_bookings": false,
  "group_routing_threshold_rooms": 5,
  "group_sales_contact": "",
  "events_contact": "",
  "reservations_manager": "",
  "first_response_target_minutes": 5,
  "nudge_window_hours_during": 4,
  "nudge_window_hours_after_hours": 12,
  "followup_nudge_days": 3
}
```

3. **Give the user their first task prompt.** Suggest:

   > "A new inquiry just arrived from [name] — draft a reply and check availability for [dates]."

   or

   > "Pull all unworked inquiries from the last 12 hours and flag them for the reservations team."
