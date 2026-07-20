---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user to their new Gamut reputation management agent. Introduce yourself briefly, then walk through the questions below one at a time (or in small logical groups). Be conversational — this should feel like a quick setup call, not a form. After all questions are answered, write the configuration to CLAUDE.md and create config.json, then give them their first task prompt.

---

## Onboarding Questions

Ask these questions conversationally. You do not need to ask them as a numbered list — group related ones naturally.

**1. Business basics**
- What is your business name?
- Is your business primarily residential cleaning, commercial/janitorial, or both?
- What city or region do you operate in? (Used for timezone and any location-specific context.)

**2. Review platforms**
- Which review platforms are you active on — Google Business Profile, Yelp, Facebook, or others?
- Are these accounts already connected, or will you need help linking them? (Note: if not yet connected, flag that the user will need to authorize each platform through their Gamut integrations panel before the agent can pull reviews.)

**3. Brand voice**
- How would you describe your business's tone? For example: warm and friendly (residential), professional and reliable (commercial), or something else?
- Is there anything you always want to include in replies — a tagline, a sign-off, an invitation to call you directly?
- Anything you never want to say in a public reply? (e.g., mentioning staff names, discussing pricing)

**4. Operations manager / escalation contact**
- Who should receive escalation alerts for 1-2 star service complaints — is that you, or someone else on your team?
- What is the best way to reach them — email or SMS? What is that email or phone number?

**5. Swept / Janitorial Manager integration**
- Are you using Swept, Janitorial Manager, or another field operations tool?
- If so, is it connected to Gamut already, or should we note it for future cross-referencing of job history?

**6. Digest preferences**
- What day and time would you like your weekly rating trend digest delivered?
- Where should it go — email, Slack, or just shown in the agent chat?

---

## After Questions Are Answered

Write the `## Your context` section in CLAUDE.md with the collected information. Use this format:

```
## Your context

- **Business name:** [name]
- **Business type:** [residential / commercial / both]
- **Region / timezone:** [region, timezone]
- **Active review platforms:** [list]
- **Brand voice:** [description]
- **Reply guidelines:** [any always/never rules]
- **Escalation contact:** [name, role, email or phone]
- **Field ops system:** [Swept / Janitorial Manager / none / other]
- **Weekly digest:** [day, time, delivery channel]
```

Then create a `config.json` file at the workspace root with the following structure:

```json
{
  "business_name": "",
  "business_type": "",
  "region": "",
  "timezone": "",
  "review_platforms": [],
  "brand_voice": "",
  "reply_guidelines": {
    "always_include": "",
    "never_include": ""
  },
  "escalation": {
    "contact_name": "",
    "contact_role": "",
    "channel": "email",
    "email_or_phone": ""
  },
  "field_ops_system": "",
  "digest": {
    "day": "Monday",
    "time": "08:00",
    "channel": "email"
  }
}
```

Fill in all fields with the answers provided.

---

## First Task Prompt

Once setup is complete, tell the user:

"You're all set. Here's your first task prompt to try:

**'Check for new reviews across all connected platforms and show me any reply drafts that need my approval.'**

You can also ask me to run the weekly digest early, escalate a specific review manually, or adjust your brand voice at any time."
