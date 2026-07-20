---
name: agent-onboarding
---

Welcome — I am going to ask you a few quick questions so I can configure your Membership Retention & Win-back agent for your specific business. This takes about five minutes and you only need to do it once. Answer as many or as few as you like; you can always update the configuration later.

---

### Business basics

1. What is your business name, and what type of business is it — yoga studio, gym, salon, med spa, or something else?
2. What city are you in, and what timezone do you operate in?
3. Roughly how many active members or recurring clients do you currently have?

---

### Booking and membership system

4. Do you use Mindbody, Boulevard, or another platform to manage memberships and bookings?
5. Is that platform already connected to Gamut? If not, can you export a member CSV so we can get the initial data loaded?
6. What types of memberships or packages do you offer — for example, monthly unlimited, class packs, annual subscriptions, or a mix?

---

### At-risk thresholds

7. What visit frequency is normal for an active member at your business — for example, two times per week, four times per month?
8. At what drop level should I flag someone as "drifting" — when their visit rate falls 40% below their own baseline, or would you prefer a different threshold?
9. How many days without a visit should trigger a "lapsed" flag — 30 days, or a number that makes more sense for your membership cycle?

---

### Retention messaging

10. How would you describe your brand voice — warm and personal, motivating and energetic, calm and professional, or something else?
11. What retention offers are you comfortable making? For example: a free guest pass, a one-month membership pause, a 20% win-back discount, a complimentary class — list whatever you are open to.
12. Is there anything you never want to offer or say in a re-engagement message? Any language, discounts, or commitments that are off the table?

---

### Alerts and digest

13. Who should receive the weekly churn-risk digest — just you, or your front desk manager or another team member as well?
14. How do you prefer to receive it — email, Slack, or in-chat?

---

## After questions are answered

Once the owner has answered the questions above, do the following:

1. **Write configuration to CLAUDE.md.** Populate the `## Your context` section at the bottom of CLAUDE.md with a structured summary of all answers, including: business name and type, city and timezone, active member count, booking platform and connection status, membership types, normal visit frequency, drift threshold (%), lapse threshold (days), brand voice description, approved retention offers, disallowed offers or language, digest recipients, and delivery channel.

2. **Create config.json.** Write a `config.json` file in the workspace root with the same data in machine-readable form, using clear keys (e.g., `businessName`, `platform`, `driftThresholdPct`, `lapseThresholdDays`, `approvedOffers`, `digestRecipients`, `digestChannel`).

3. **Give the user their first example task prompt.** After confirming that configuration is saved, say:

   "You are all set. Here is a prompt to get started:

   'Pull today's membership data and show me every member currently flagged as at-risk, grouped by tier. Draft a retention message for each drifting or lapsed member and queue them for my review.'"
