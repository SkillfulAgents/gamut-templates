---
name: agent-onboarding
---

Welcome to the Restaurant/QSR - Review & Reputation Replies agent. This onboarding session will set up everything the agent needs to monitor your reviews, draft replies in your voice, escalate serious complaints, and deliver your weekly rating digest.

We will go through a short set of questions. Answer as fully or briefly as you like - you can always update the config later. Let's get started.

---

**Question 1 - Restaurant basics**

What is your restaurant name, concept type (e.g., fast-casual, full-service, QSR chain), and how many locations are you managing? If you have multiple locations, list each location name or identifier.

---

**Question 2 - Platform listings**

Which review platforms are active for your restaurant? For each platform you use, provide the listing ID or profile URL:
- Google Business Profile location ID or URL
- Yelp business page URL or business ID
- TripAdvisor listing URL or location ID

If you have multiple locations, list the IDs for each.

---

**Question 3 - Toast POS access**

Do you use Toast POS? If yes, provide your Toast API credentials (client ID and client secret) and the location GUID(s) for your restaurant(s). If you do not use Toast or want to skip the POS cross-reference feature, just say "skip."

---

**Question 4 - Brand voice and reply guidelines**

Describe the tone and personality you want in every public reply. For example: Is the voice casual and neighborhood-friendly, or polished and upscale? Do you want replies to feel like they come from the owner personally, or from the management team? Are there any phrases or approaches you specifically want to avoid? If you have example replies you like, paste one or two here.

---

**Question 5 - Escalation contacts**

When the agent detects a food safety concern, allergy complaint, or threatening review, who should be notified immediately? Provide:
- Manager name and email address
- Slack handle or channel (if applicable)
- Any additional triggers beyond the defaults (food safety, allergy, threats) that should trigger escalation at your restaurant

---

**Question 6 - Reply workflow preferences**

How would you like reply approvals to work?
- Should every draft require individual approval before publishing, or can you approve straightforward positive-review thank-yous in batch?
- What is your target reply time for 1-star and 2-star reviews (e.g., within 4 hours, within 24 hours)?
- Are you comfortable with the agent flagging any unanswered review older than 48 hours as overdue?

---

**Question 7 - Weekly digest delivery**

Who should receive the weekly Monday rating digest? List names and email addresses. If you want the digest delivered to a Slack channel instead of (or in addition to) email, provide the channel name.

---

**Question 8 - Compensation and public offer policy**

Should the agent ever offer a discount, gift card, or complimentary item in a public reply? If yes, under what conditions and up to what value? If no, the agent will always direct compensation conversations to a private channel (e.g., "please reach out to us directly"). This policy will be enforced in every draft.

---

## After collecting answers

Once the user has answered all questions, do the following:

### 1. Write config.json

Create a `config.json` file at the workspace root with this structure:

```json
{
  "restaurant": {
    "name": "",
    "concept_type": "",
    "locations": [
      {
        "id": "",
        "name": "",
        "google_location_id": "",
        "yelp_business_id": "",
        "tripadvisor_location_id": ""
      }
    ]
  },
  "integrations": {
    "google_business_profile": {
      "enabled": true,
      "credentials": {
        "client_id": "",
        "client_secret": "",
        "refresh_token": ""
      }
    },
    "yelp": {
      "enabled": true,
      "api_key": ""
    },
    "tripadvisor": {
      "enabled": true,
      "api_key": ""
    },
    "toast_pos": {
      "enabled": false,
      "client_id": "",
      "client_secret": "",
      "location_guids": []
    }
  },
  "monitoring": {
    "poll_interval_hours": 4,
    "overdue_reply_threshold_hours": 48
  },
  "escalation": {
    "manager_name": "",
    "manager_email": "",
    "manager_slack": "",
    "triggers": [
      "food safety",
      "food poisoning",
      "allergy",
      "raw",
      "undercooked",
      "foreign object",
      "health department",
      "threatening"
    ]
  },
  "reply_workflow": {
    "batch_approve_positive": false,
    "target_reply_hours_negative": 24,
    "target_reply_hours_positive": 48,
    "allow_public_compensation_offers": false,
    "max_public_offer_value_usd": 0
  },
  "digest": {
    "schedule": "monday_morning",
    "recipients_email": [],
    "recipients_slack_channel": ""
  },
  "brand_voice": {
    "tone_description": "",
    "example_replies": [],
    "avoid_phrases": []
  }
}
```

Fill in all fields from the user's answers. Leave fields blank or as defaults for anything the user skipped.

### 2. Update CLAUDE.md

Open `CLAUDE.md` and replace the `<!-- Filled in during onboarding -->` comment in the `## Your context` section with a plain-English summary that includes:
- Restaurant name and concept type, number of locations
- Active review platforms and any location-specific notes
- Brand voice description (2-3 sentences from Question 4)
- Escalation contact name and preferred channel
- Reply workflow: approval mode, target latency, compensation policy
- Digest recipients and delivery channel

Write this as a short paragraph or a simple bulleted list - not JSON. The agent reads this section directly.

### 3. Confirm setup and suggest first task

Tell the user setup is complete and suggest this first task to try:

"Show me all unanswered reviews from the last 7 days, flag any that need escalation, and draft replies for the 1-star and 2-star reviews."
