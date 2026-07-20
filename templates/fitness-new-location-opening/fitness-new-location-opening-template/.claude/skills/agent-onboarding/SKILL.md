---
name: agent-onboarding
---

# Agent Onboarding — Fitness/Wellness/Salon/Spa New-Location Opening

Welcome to your Gamut new-location opening agent. To build your opening checklist and configure your daily tracking, I need a few details about the location you are opening. I will ask the questions in sections — just answer each one and I will handle the rest.

---

## Section 1: Location basics

1. What is the name and type of the new location (yoga studio, salon, gym, med spa, etc.)?
2. What city will it be in?
3. What is the planned opening date?
4. Has the lease been signed, or is it still in negotiation?

---

## Section 2: Current status

5. What phase are you in today? (site selection, signed lease, build-out underway, equipment ordered, etc.)
6. What is the single most important item that needs to happen in the next two weeks?

---

## Section 3: Key milestones

7. When do you need to submit for your business license and any required permits?
8. When is the build-out or renovation expected to be complete?
9. When will equipment be installed?
10. When does staff need to be hired and trained?
11. When are you launching pre-sale memberships?

---

## Section 4: Vendors and contractors

12. Do you have a general contractor engaged? What is the build-out completion date?
13. Who is your equipment vendor, and when is delivery expected?
14. Any other key vendors to track (POS, signage, AV, etc.)?

---

## Section 5: Systems setup

15. Do you use Mindbody or Boulevard at your existing location(s)?
16. Will the new location be a separate account or added to your existing setup?
17. Are there system integrations that need to be configured before opening?

---

## Section 6: Staffing

18. How many staff roles do you need to hire for opening (instructors, front desk, management)?
19. Do you have a target date for completing hiring?

---

## Section 7: Pre-sale and marketing

20. Are you running a pre-sale membership campaign before opening? If so, what is your target number of pre-sale members?
21. What channels will you use (social, email, local outreach)?
22. Where should the daily progress brief go — email, Slack, or in-chat?

---

## After questions are answered

Once the owner has answered all onboarding questions:

1. **Write configuration to CLAUDE.md.** Populate the `## Your context` section at the bottom of `CLAUDE.md` with a structured summary including: location name and type, city, planned opening date, lease status, current phase, most urgent near-term item, all key milestone dates (permits, build-out, equipment, staffing, pre-sale launch), vendor and contractor details, software platform (Mindbody or Boulevard) and account setup notes, staffing headcount and hiring target date, pre-sale membership target (if applicable), marketing channels, and preferred daily brief delivery channel.

2. **Create config.json** in the workspace root with the same data in structured JSON form. Include at minimum:
   - `locationName`
   - `locationType`
   - `city`
   - `plannedOpeningDate`
   - `leaseStatus`
   - `currentPhase`
   - `mostUrgentItem`
   - `milestones` (object with keys: permitsDeadline, buildOutComplete, equipmentInstall, hiringComplete, preSaleLaunch)
   - `vendors` (array of objects with name, role, keyDate)
   - `softwarePlatform`
   - `softwareSetupNotes`
   - `staffRolesNeeded`
   - `hiringTargetDate`
   - `preSaleTarget` (number or null)
   - `marketingChannels`
   - `briefDeliveryChannel`

3. **Give the owner their first example task prompt.** After confirming setup is complete, say:

   > "You are all set. Here is a prompt to get started:
   >
   > *'Generate the full opening checklist for [location name] organized by phase, assign the milestone dates we discussed, and flag the three most urgent items I need to move on this week.'*"
