# Challenge 07: Security Investigation & Threat Response with Microsoft Security Copilot

**Estimated Duration:** 45 minutes

---

## Scenario

Your response team has already implemented and reviewed key Microsoft Purview controls across labeling, DLP, insider risk, posture management, and governance. In this final challenge, you will use Microsoft Security Copilot as an investigation accelerator to assemble the incident story behind the recent data exposure event. Your goal is to validate that the Microsoft Purview source is available, use natural-language prompting to summarize DLP and Insider Risk findings, generate a KQL-based investigation path, and produce a concise incident report that clearly distinguishes evidence, conclusions, and limitations.

---

## What You Need to Do

Use Microsoft Security Copilot, paired with Microsoft Purview evidence, to build a defensible end-to-end investigation narrative:

1. Set up Security Copilot and verify the Microsoft Purview plugin is available
2. Summarize a DLP alert using natural-language prompts and validate against source evidence
3. Produce a stakeholder-ready Insider Risk case summary
4. Generate and critically review a KQL investigation query
5. Draft a structured incident report that documents Copilot's limitations

---

## Task 1: Open Microsoft Security Copilot and Verify the Microsoft Purview Plugin

**Portals:**
- Microsoft Purview: [https://purview.microsoft.com](https://purview.microsoft.com)
- Microsoft Security Copilot: [https://securitycopilot.microsoft.com](https://securitycopilot.microsoft.com)

Sign in to both portals using the lab credentials above. Confirm your Azure subscription and tenant context in a separate tab at [https://portal.azure.com](https://portal.azure.com).

### Workspace Setup

If prompted to configure a new Security Copilot workspace, use the following settings:

| Setting | Value |
|---|---|
| Workspace name | Hackathon-Workspace <inject key="DeploymentID" enableCopy="false"></inject> |
| Data storage location | United States |
| Capacity name | Hackathon-Workspace <inject key="DeploymentID" enableCopy="false"></inject>-Capacity |
| Prompt evaluation location | Australia |
| Capacity region | Australia East |
| Contributors | No one. Add them later |

Accept the default data-sharing, Microsoft 365 access, and Purview audit logging settings on the subsequent setup pages, then click **Finish** to open the Security Copilot workspace.

### Verify the Purview Plugin

In the Security Copilot prompt box, enter:

```text
Show me the Microsoft Purview capabilities available in this session and tell me which ones can help investigate DLP alerts and Insider Risk activity.
```

Submit and review the response to confirm the Purview source is active.

> **Important:** This challenge assumes Security Copilot readiness and Purview plugin availability were pre-staged for the tenant. If the Purview source is missing entirely, pause and notify the facilitator before continuing.

---

## Task 2: Summarize a DLP Alert with Natural-Language Prompts

### Step 1 — Gather the Source Evidence

In Microsoft Purview, navigate to **Solutions** > **Data Loss Prevention** and open one recent DLP alert related to the seeded exposure scenario.

Record in your notes:
- Alert name, severity, impacted user
- Alert/event identifier (if available)
- Triggering activity (from the **Events** and **Details** panes)

### Step 2 — Prompt Copilot

Return to **Microsoft Security Copilot** and submit:

```text
Summarize the Microsoft Purview DLP alert [alert name or alert ID]. Include the likely data involved, the triggering activity, affected user, severity, and recommended next investigation steps.
```

Compare the response against the original alert details in Purview. Then run a follow-up prompt:

```text
Explain this DLP alert in plain language for a compliance manager and identify the top three risks suggested by the evidence.
```

### Step 3 — Validate and Capture Evidence

Note any uncertain facts, missing fields, or assumptions in the Copilot response. Save the Copilot output and a screenshot of the DLP alert details to your evidence folder.

> **Tip:** Strong prompts include concrete identifiers — alert title, user, timeframe, or severity. If your first prompt returns a vague answer, refine it with specifics from the alert details page.

---

## Task 3: Create an Insider Risk Case Summary for Compliance Stakeholders

### Step 1 — Gather the Source Evidence

In Microsoft Purview, navigate to **Insider Risk Management** and open **Alerts** or **Cases**, depending on what is pre-staged. If needed, use **Actions** > **Confirm alerts & create case** to formalize a case.

Review the **Alerts**, **User activity**, **Activity explorer**, and **Case notes** tabs, and record: the risky user, policy/indicator context, main risky activities, and current case status.

### Step 2 — Prompt Copilot

Return to **Microsoft Security Copilot** and submit:

```text
Summarize the Insider Risk case for a compliance audience. Focus on who is involved, what risky behavior was observed, what data may have been exposed, and what next steps the investigation team should take.
```

If the response is too technical, refine with:

```text
Rewrite the summary in executive-ready language with sections for Incident Overview, Evidence, Business Impact, and Recommended Actions.
```

### Step 3 — Validate and Capture Evidence

Compare the Copilot summary against the actual case details in Purview. Save the final summary to your investigation notes, and add a short analyst note stating whether the summary was complete, partially complete, or required manual correction.

<validation step="Final Investigation Evidence"/>

---

## Task 4: Generate and Review a KQL Investigation Query

### Step 1 — Generate the Query

In **Microsoft Security Copilot**, submit:

```text
Generate a KQL query I can use to investigate related risky user activity for this incident. Include a brief explanation of what each filter is doing and focus on audit or data security events tied to the user and timeframe in this case.
```

### Step 2 — Review Before Use

Review the generated query carefully:
- Confirm whether it references realistic tables, fields, users, and timestamps for your environment
- If a hunting/log workspace is available, copy the query in and run it
- If live execution isn't available, perform a desk review instead: check filter logic, identify needed table/field adjustments, and note what evidence the query is intended to return

### Step 3 — Refine if Needed

```text
Adjust the KQL query so it is easier for an analyst to modify for another user or date range, and explain any assumptions you made.
```

Save the generated query and your review comments to the evidence folder.

> **Note:** Treat Copilot-generated KQL as a starting point. Validate table names, schema assumptions, and time filters before using the query operationally.

---

## Task 5: Draft an Incident Report and Evaluate Copilot Limitations

### Step 1 — Set Up the Report Structure

Create a document with the following headings:
- Incident title
- Executive summary
- DLP findings
- Insider Risk findings
- KQL/audit investigation notes
- Containment and remediation actions
- Known limitations and analyst validation notes

### Step 2 — Generate a Draft with Copilot

```text
Create a structured incident report based on a Purview investigation involving a DLP alert and an Insider Risk case. Include executive summary, evidence observed, likely impact, remediation actions, and open questions that require analyst verification.
```

Use the response as a starting draft, then manually edit it to match the actual evidence you reviewed in Tasks 2–4.

### Step 3 — Document Limitations

Add at least one limitation or reliability boundary you observed, for example:
- Copilot needed more specific identifiers to return a useful answer
- Copilot produced a summary that omitted important case context
- The generated KQL required manual correction before it could be trusted
- Plugin data availability or role scoping limited the depth of results

Add a final conclusion stating whether Copilot accelerated the investigation, and where analyst review remained essential.

### Step 4 — Save and Finalize

Save the report as **Challenge7-Incident-Report.docx** or **Challenge7-Incident-Report.txt** in your evidence folder.

**Confirm your final evidence set includes:**
- Plugin verification screenshot
- DLP alert summary
- Insider Risk case summary
- KQL query and review notes
- Final incident report

<validation step="Final Investigation Evidence"/>

---

## Summary

In this challenge, you used Microsoft Security Copilot with Microsoft Purview data to accelerate investigation and response. You verified plugin availability, summarized a DLP alert, translated an Insider Risk case into stakeholder-ready language, generated a KQL investigation path, and compiled a final incident report. Most importantly, you validated Copilot output against source evidence and documented its limitations, demonstrating a realistic and defensible investigation workflow for regulated environments.
