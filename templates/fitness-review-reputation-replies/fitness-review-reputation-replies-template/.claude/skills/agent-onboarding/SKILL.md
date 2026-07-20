---
name: agent-onboarding
---

# Agent Onboarding

Welcome — let's get your Review & Reputation Replies agent set up. I'll ask you a few quick questions so the agent knows your business, your voice, and who to contact when something needs attention. This takes about 5 minutes.

---

## Business basics

1. What is your business name and type? (For example: yoga studio, CrossFit gym, blow-dry bar, med spa, day spa, nail salon, etc.)
2. How many locations do you have? If multiple, please list the names or cities.
3. What city or region are you based in?

---

## Review platforms

4. Which review platforms are you active on — Google Business Profile, Yelp, Facebook, ClassPass, Mindbody Marketplace, or others?
5. Are those accounts already connected to Gamut, or will you need help linking them?

---

## Brand voice

6. How would you describe your business's tone — warm and personal, motivating and energetic, serene and professional, or something else in your own words?
7. Is there a phrase or sign-off you always want included in your replies? (For example: "See you in the studio," or "With gratitude, the [Name] team.")
8. Is there anything you never want to mention publicly in a review reply — specific staff names, pricing, internal policies, or anything else?

---

## Escalation contact

9. Who handles service failure escalations — you personally, your studio manager, or someone else?
10. What is the best way to reach them for urgent alerts — email address or Slack handle?
11. Is Mindbody or Boulevard connected to your Gamut workspace? (This lets the agent pull appointment history when cross-referencing a complaint.)

---

## Digest preferences

12. What day and time should your weekly rating digest arrive? (Default: Monday at 8 AM local time.)
13. Where should it be delivered — email, Slack, or here in chat?

---

## After questions are answered

Once the owner or manager has answered all questions above, do the following:

1. **Write configuration to CLAUDE.md.** Under the `## Your context` section, fill in a structured summary including:
   - Business name, type, and locations
   - Active review platforms and connection status
   - Brand voice description and sign-off phrase
   - Topics and details to never mention publicly in replies
   - Escalation contact name and email/Slack handle
   - Whether Mindbody or Boulevard is connected
   - Weekly digest schedule and delivery channel

2. **Create `config.json`** in the workspace root with the same information in machine-readable form, using keys: `businessName`, `businessType`, `locations`, `reviewPlatforms`, `brandVoice`, `signOff`, `neverMention`, `escalationContact`, `escalationChannel`, `appointmentSystem`, `digestDay`, `digestTime`, `digestChannel`.

3. **Confirm setup is complete** and give the user their first example task prompt:

   *"You're all set. Try this to get started:*

   **'Check for any new reviews from the past 7 days and show me the reply drafts.'**

   *The agent will pull reviews from your connected platforms, classify them, flag any escalations, and present draft replies for your approval before anything goes live."*
