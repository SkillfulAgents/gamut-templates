---
name: agent-onboarding
---

# Agent Onboarding

Welcome — let's configure your Hospitality/Hotels Bid and Proposal Drafter. I'll ask about your property, your proposal library, connected systems, and how you want drafts delivered. About 8 minutes.

---

## Property basics

1. What is your property's name, brand affiliation (if any), location, and primary market segments (corporate groups, weddings, social events, association conferences, sports teams)?
2. Roughly how many guest rooms do you have, and what are your main meeting and event spaces (names, capacities, and primary setup types)?

---

## RFP intake

3. How do group RFPs and event inquiries typically arrive — through Opera or Cloudbeds, Cvent, email, or a combination? Which system should the agent monitor first?
4. Is there a specific email inbox or CRM queue where new inquiries land?

---

## Proposal library and rate cards

5. Where are your past contracts and approved proposal templates stored — Google Drive, SharePoint, Opera, or another system? Please share the folder path or link.
6. Where are your current rate cards, group pricing grids, and catering menus? Are they in the same location, or a separate file?
7. Do you have approved boilerplate sections (property overview, contract terms, cancellation policy) in a specific document?

---

## Pricing and approval workflow

8. Is there a minimum room block or F&B minimum below which the property typically charges meeting room rental? (This helps the agent include or exclude rental fees in draft proposals.)
9. Should the agent include proposed group rates in the draft (using the rate card), or always mark pricing as a placeholder for revenue management to confirm?

---

## Output and delivery

10. Where should draft proposals and checklists be saved — a specific Drive folder, Opera document library, or another location?
11. Who is the sales manager or director who should be notified when a draft is ready? Provide their name and Slack handle or email.

---

## After Questions Are Answered

1. **Update CLAUDE.md** with: property name, brand, market segments, room count, meeting spaces summary, intake source, proposal library location, rate card location, boilerplate location, pricing policy, output folder, and sales manager contact.

2. **Create config.json** at `.claude/skills/agent-onboarding/config.json`:

```json
{
  "property_name": "",
  "brand": "",
  "market_segments": [],
  "room_count": 0,
  "meeting_spaces": [],
  "rfp_intake_source": "opera | cloudbeds | cvent | email | other",
  "rfp_intake_connected": true,
  "proposal_library_path": "",
  "rate_card_path": "",
  "boilerplate_path": "",
  "include_rates_in_draft": false,
  "output_folder": "",
  "sales_manager": ""
}
```

3. **Give the user their first task prompt.** Suggest:

   > "Draft a proposal for [client name] — [N] rooms, [event type], [dates]."

   or

   > "A new RFP just arrived in the Cvent queue — draft a response."
