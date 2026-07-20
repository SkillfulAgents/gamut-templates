# Skill: agent-onboarding

## Purpose

Walk the studio owner or manager through a short setup conversation so the Speed-to-Lead & Booking agent has everything it needs to start responding to and converting leads immediately. Collect configuration details conversationally — ask in natural groupings, not as a form dump.

---

## Onboarding conversation flow

Greet the user warmly and explain what you're setting up. Then work through the sections below in order. Ask each group of related questions together so the conversation feels efficient.

---

### Section 1: Lead channels

Ask:
- Where do your leads currently come from? (Check all that apply: website contact form or landing page, direct email to the studio inbox, ClassPass, Mindbody Marketplace, Instagram DM, Facebook Messenger, Yelp, Google Business messages, or somewhere else?)
- For each active channel: what's the specific email address, form endpoint, or integration that receives leads?
- Is there one primary channel that drives most of your leads, or are they fairly spread out?

---

### Section 2: Booking system

Ask:
- Do you use **Mindbody** or **Boulevard** for your schedule and bookings? (Or both, for multi-brand or multi-location?)
- What is your site/location name or ID in the system?
- If multi-location: list locations and confirm whether leads should be routed to a specific location or matched by the lead's preference
- Are there any classes or services that should never be booked through the agent without manual review first? (e.g., premium packages, medical consultations, private sessions over a certain price)

---

### Section 3: Intro offer and services

Ask:
- Do you currently have a new client intro offer? (e.g., first class free, $X for your first month, complimentary consultation, new client discount)
  - If yes: what are the terms — what does it include, what's the expiration, any exclusions?
- What are your main class formats or service types? (e.g., hot yoga, reformer pilates, cycling, barre, deep tissue massage, blowout, color, facial — list what you want the agent to know about)
- Are there any services that require a consultation or intake form before booking?

---

### Section 4: Brand voice

Ask:
- How would you describe the voice you want the agent to use when replying to leads? (e.g., warm and encouraging, professional and polished, casual and fun, motivational)
- Is there anything you'd never want the agent to say or promise? (e.g., specific pricing commitments, claims about results)
- Can you share an example of how you'd personally reply to a lead inquiry — even a rough version? This helps the agent match your tone.
- Should the replies come from your name, the studio name, or a team role (e.g., "the team at [Studio]")?

---

### Section 5: Follow-up preferences

Ask:
- How long should the agent wait before sending a follow-up nudge if a lead goes silent? (Default is 24 hours — does that work?)
- For leads that started a conversation but then went quiet, how long should the agent wait before a check-in message? (Default is 48 hours after last reply)
- After one follow-up with no response, the agent marks the lead cold and stops. Is there any scenario where you'd want a second follow-up before marking cold?

---

### Section 6: Reporting preferences

Ask:
- Where should the weekly lead-to-booking summary be sent — email, Slack/Teams, or a doc/sheet?
- What day and time works for the weekly summary? (Default: Monday morning)
- Are there any specific metrics that matter most to you? (e.g., conversion rate by lead source, intro offer redemption, response time)

---

## After Questions Are Answered

Summarize the configuration back to the user in plain language before saving:

- Lead channels being monitored
- Booking system and location(s)
- Intro offer details and service menu
- Voice and tone guidelines, sender name
- Follow-up timing windows
- Reporting destination and schedule

Ask: "Does this look right, or anything to adjust before I save it?"

Once confirmed:
1. Write all configuration details into the `## Your context` section of `CLAUDE.md`
2. Confirm to the user: "You're all set. The agent is ready to respond to new leads. You can test it now by forwarding a lead email or form submission, or by saying: 'A new lead just came in from [source] — her name is [name] and she's interested in [class/service]. Draft the first reply.'"
