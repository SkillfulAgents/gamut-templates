---
name: agent-onboarding
---

Welcome - let's get your Invoice & AR Chase agent set up for your construction business. This takes about 5 minutes. Your answers will be saved so the agent knows how to connect to your billing systems, what your payment terms are, and who to keep in the loop.

Please answer the following questions. You can answer all at once or one at a time.

1. **Company basics** - What is your company name, and how would you describe your work? (For example: commercial general contractor, specialty subcontractor - electrical, CM at risk, or a mix.) What is your typical active project count and average contract value?

2. **Accounting and billing system** - Which system do you use for invoicing and AR? For example: Sage 300 CRE, Viewpoint Vista, Foundation Software, Procore Financials, QuickBooks, or a combination. Please include version if known.

3. **Project management system** - Do you use Procore for project management and pay application workflow? If so, which Procore modules do you use (Core, Financials, Project Financials)?

4. **Billing format** - What billing format do you use most often? AIA G702/G703 pay applications, standard invoices, or a mix depending on contract type?

5. **Payment terms and cycles** - What are your standard payment terms (e.g., net-30 from approval, pay-when-paid, net-45)? What is the typical owner pay cycle in your market?

6. **Outreach ownership** - Who sends AR follow-up messages - the project manager, controller, or the principal/owner? The agent will write in their voice.

7. **States of operation** - Which states do you work in most often? This matters for lien rights language and prompt payment statute deadlines.

8. **Weekly digest recipients** - Who should receive the weekly cash and AR digest? Please provide names and email addresses.

---

## After collecting answers

Save the configuration to `config.json` at the workspace root:

```json
{
  "company": {
    "name": "",
    "type": "",
    "typicalProjectCount": null,
    "averageContractValue": ""
  },
  "systems": {
    "accounting": "",
    "accountingVersion": "",
    "projectManagement": "",
    "procoreModules": []
  },
  "billing": {
    "primaryFormat": "",
    "paymentTerms": "",
    "ownerPayCycle": ""
  },
  "outreach": {
    "senderRole": "",
    "senderName": ""
  },
  "statesOfOperation": [],
  "digestRecipients": []
}
```

Then update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-English paragraph summarizing the company name, project type, billing systems, payment terms, outreach voice, operating states, and digest recipients.

Once both files are saved, confirm setup is complete and suggest a first task: "You're set up. To get started, export your open AR from [system name] and paste it here, or connect the system and ask me to pull open receivables older than 30 days."
