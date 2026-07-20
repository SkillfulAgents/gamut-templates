# Skill: agent-onboarding

## Purpose

Walk the owner through a conversational setup interview to gather everything the Review & Reputation Replies agent needs to start monitoring and responding. Ask questions in a natural, grouped conversation — not a form dump. At the end, write the configuration to CLAUDE.md and create config.json, then give the owner their first ready-to-use task prompt.

---

## How to Run This Skill

When the user types `run agent-onboarding`, begin the onboarding conversation below. Work through each section conversationally, pausing for answers before moving to the next group. You do not need to ask every sub-question if the owner has already answered it in passing.

---

## Onboarding Questions

### Section 1 — Business Basics

Start here:

> "Welcome — let's get your Review & Reputation agent set up. I'll ask a few quick questions so I can start monitoring your reviews and drafting replies in your voice. This should take about 5 minutes.
>
> First, tell me about your business:"

Ask:
1. What is the name of your business? (brand name)
2. What type of business is it? (fitness studio, yoga/pilates, gym, hair salon, barbershop, blow-dry bar, nail salon, spa, med spa, or other — pick the closest)
3. How many locations do you have? (If more than one, list the location names — e.g., "Downtown" and "Westside.")
4. Roughly how many Google reviews do you have today, and what is your current Google rating? (Approximate is fine.)

---

### Section 2 — Review Platforms

> "Now let's connect your review platforms."

Ask:
1. Which platforms are you active on — Google Business Profile, Yelp, Facebook, or others? (List all that apply.)
2. For each platform: have you claimed and verified your business listing? (This is required for reply access.)
3. Do you currently have a process for replying to reviews, or are you starting fresh?
4. Is there a platform where you get the most reviews — or one where a negative review would hurt most?

---

### Section 3 — Brand Voice

> "This is one of the most important parts of setup — your reply voice needs to sound like you, not a corporate template."

Ask:
1. How would you describe the personality of your brand in 2–3 words? (e.g., "warm and encouraging," "upscale and polished," "approachable neighborhood gym," "fun and high-energy")
2. Are there any words or phrases you always use — or that you would never want to see in a reply? (e.g., "We say 'guests' not 'customers'" or "never say 'unfortunately'")
3. How formal do you want the replies to feel on a scale of 1–5? (1 = very casual/conversational, 5 = professional/polished)
4. Do you want replies to sign off with a name or a title? (e.g., "— Sarah, Owner" or "— The [Brand] Team" or no sign-off)

---

### Section 4 — Escalation and Management

> "Let's set up your escalation flow for negative reviews."

Ask:
1. Who should be alerted first when a 1-star or serious 2-star review comes in? (Name and role — could be you, a GM, or a front desk manager.)
2. Is there a secondary escalation contact for owner-level issues (injury mentions, legal threats, discrimination claims)?
3. Which platform does your team use for internal alerts? (e.g., email, text, Slack, or just within Gamut)
4. For escalated complaints: do you use Mindbody or Boulevard to look up client appointment records? (This helps cross-reference the visit and make your reply more credible.)
5. If yes: who has access to run those lookups — the manager, you, or a specific staff member?

---

### Section 5 — Weekly Digest Preferences

> "Almost done — a few preferences for your weekly report."

Ask:
1. What day and time do you want your weekly Rating Trend Digest? (Default: Monday morning.)
2. Do you want the digest to include per-location breakdowns, or just a brand-level summary?
3. Is there a specific rating threshold you're targeting — for example, "I want to get to 4.7 stars on Google"? (I'll track your progress toward it.)

---

## After Questions Are Answered

Once all sections are complete:

### Step 1 — Write ## Your context to CLAUDE.md

Append the following section to the bottom of CLAUDE.md, replacing the `<!-- Filled in during onboarding -->` placeholder:

```
## Your context

**Business:** [Business name] — [Business type]
**Locations:** [List of location names, or "Single location"]

**Review platforms:** [Google / Yelp / Facebook / Other — list all active]
**Highest-priority platform:** [Platform where reviews matter most]
**Existing review volume:** [Approximate count and current Google rating]

**Brand voice:** [2-3 word description]
**Tone level:** [1–5 scale — e.g., "3 — balanced, conversational but professional"]
**Voice notes:** [Any specific phrases to use or avoid]
**Reply sign-off:** [e.g., "— The [Brand] Team" / "— [Owner name], Owner" / None]

**Primary escalation contact:** [Name] — [Role]
**Owner escalation contact:** [Name or same as primary]
**Alert channel:** [Email / Text / Slack / Gamut]
**Client lookup system:** [Mindbody / Boulevard / N/A]
**Lookup access:** [Who runs lookups]

**Weekly digest:** [Day and time]
**Digest format:** [Brand-level only / Per-location breakdown]
**Rating goal:** [Target rating, or "Not set"]
```

### Step 2 — Create config.json

Create a file at `config.json` in the workspace root with the following structure:

```json
{
  "business_name": "[Business name]",
  "business_type": "[Business type]",
  "locations": ["[Location 1]", "[Location 2]"],
  "platforms": {
    "google": { "active": true, "verified": true },
    "yelp": { "active": true, "verified": true },
    "facebook": { "active": true, "verified": true }
  },
  "brand_voice": {
    "description": "[2-3 word brand personality]",
    "tone_level": 3,
    "phrases_to_use": [],
    "phrases_to_avoid": [],
    "sign_off": "[Sign-off text or null]"
  },
  "escalation": {
    "primary_contact": {
      "name": "[Name]",
      "role": "[Role]",
      "channel": "[email|text|slack|gamut]"
    },
    "owner_contact": {
      "name": "[Name]",
      "channel": "[email|text|slack|gamut]"
    }
  },
  "client_lookup": {
    "platform": "[mindbody|boulevard|none]",
    "access_owner": "[Name]"
  },
  "weekly_digest": {
    "day": "monday",
    "time": "09:00",
    "per_location_breakdown": false
  },
  "rating_goal": {
    "platform": "google",
    "target": null
  },
  "review_log": []
}
```

Fill in all values from the onboarding answers. Set platform `active` and `verified` to `false` for any platform the owner is not using or has not verified. Set `rating_goal.target` to the number the owner provided, or `null` if not set.

### Step 3 — Give the First Example Task Prompt

Close onboarding with:

> "You're all set. Here's your first task — just send this (or something like it) to get started:
>
> **'We have a new 1-star Google review from someone who says our front desk ignored them when they checked in. Can you classify it, draft two reply options in our voice, and flag it for [manager name] to look up the appointment in [Mindbody/Boulevard]?'**
>
> I'll classify the review, draft two on-brand reply options for your approval, and prepare the escalation note so [manager name] knows exactly what to look up."
