# Challenge 03: Insider Risk Management & Data Security Investigations

**Estimated Duration:** 1 hour 15 minutes

---

## Scenario

A member of the Titan Journey program team may have mishandled sensitive information following recent oversharing events and unusual collaboration behavior. Your response team must validate Microsoft Purview Insider Risk Management readiness, review exfiltration-related signals, triage a risky user alert, and escalate the matter into a formal investigation so the organization can document impact and remediation.

---

## What You Need to Do

Review Insider Risk Management configuration and build a complete investigation workflow:

1. Validate Insider Risk Management readiness and available signals
2. Create an exfiltration-focused insider risk policy
3. Triage an alert and analyze the user activity timeline
4. Create a formal case and escalate to Data Security Investigations
5. Create a notice template and compile investigation evidence

---

## Task 1: Sign In and Review Insider Risk Management Readiness

**Portal:** [https://purview.microsoft.com](https://purview.microsoft.com)

Sign in using the lab credentials above. Navigate to **Solutions** > **Insider Risk Management** and confirm the following areas are accessible in the left navigation:

- Policies
- Reports > Alerts
- Reports > Cases

Review the **Policies** page — note any existing policies. Review the **Alerts** page — note whether pre-staged alerts are available.

Capture a screenshot of the Insider Risk Management dashboard and save it to your evidence folder, including the Deployment ID in the filename.

> **Important:** Insider Risk Management depends on prerequisites such as roles, indicators, and signal sources. If alerts or policies are pre-staged in your environment, use them rather than waiting for new telemetry to propagate.

---

## Task 2: Create an Exfiltration-Focused Insider Risk Policy

Navigate to **Insider Risk Management** > **Policies** > **Create policy** > **Custom policy**.

### Policy Configuration

| Setting | Value |
|---|---|
| Template | Data leaks |
| Policy name | `Titan Journey Exfiltration Review` |
| Description | Detects risky data exfiltration and oversharing behavior for the Titan Journey hackathon scenario. |
| Scope | All users, groups, and adaptive scopes |
| Content priority | Prioritize content — add **Finance** trainable classifier |
| Triggering event | User matches a DLP policy → **Hackathon - Financial DLP** |

During the **Indicators** step, if a warning appears that required indicators are turned off, click **Turn on indicators** and save the selection before continuing.

After creation, verify the policy appears in the list with a **Healthy** status.

> **Note:** Policy health warnings can appear when indicators, triggers, or related dependencies are incomplete. In the hackathon tenant, use what is already prepared rather than remediating every backend dependency.

> **Tip:** If a pre-created policy with active alerts already exists, you may use it for the remaining tasks alongside any new policy you create.

---

## Task 3: Triage an Alert and Analyze the User Activity Timeline

Navigate to **Insider Risk Management** > **Alerts**. Filter for **Needs review** status if needed and open the highest-severity alert available.

**Review and record the following in your notes:**
- User involved
- Policy associated with the alert
- Triggering event and alert severity
- Activity that generated the alert

**Investigation steps:**
1. If a **Summarize** or **Summarize with Copilot** option is available, use it and record the result
2. Open the **Activity explorer** tab and inspect the timeline — filter for exfiltration or sequence-related events
3. Open the **User activity** tab and review historical risk patterns (repeated downloads, external sharing, sequence activities, cumulative exfiltration indicators)
4. If content preview is available, review enough detail to assess whether activity appears benign, accidental, or suspicious

**Record your preliminary conclusion:**
- What data or content appears to be involved?
- What actions increased the risk score?
- Does the activity justify escalation to a formal case?

Save at least one screenshot of the alert details or user activity timeline for your final evidence package.

> **Important:** Insider Risk Management generates a single aggregated alert per user and adds new insights over time. Understand the full alert narrative, not just the first event in isolation.

<validation step="Insider Risk / investigation artifacts"/>

---

## Task 4: Create a Case and Escalate to Data Security Investigations

### Part A — Create the Case

From the alert details or alerts dashboard, select the triaged alert and choose **Actions** > **Confirm alerts & create case**.

| Setting | Value |
|---|---|
| Case name | `Titan Journey Insider Risk Case - Challenge 3` |
| Comments | Summarize the suspicious behaviors observed during triage |

After creation, open **Cases** and select the new case. Review available tabs (Alerts, User activity, Activity explorer, Case notes) and add a case note summarizing your current investigation finding.

### Part B — Escalate to Data Security Investigations

From the case action toolbar, select **Case actions** > **Investigate data security with AI**.

| Setting | Value |
|---|---|
| Investigation name | TitanJourney-DSI-Challenge3-<inject key="DeploymentID"></inject> |
| Description | Evaluate potential data exfiltration and content exposure associated with the insider risk case |
| Investigation scope | Keep relevant items from the case selected |
| Additional AI context | `Investigate whether the scoped files or messages contain regulated, financial, personal, or confidential project data that would increase breach impact.` |

After creation, verify the investigation appears in the Data Security Investigations dashboard and record the investigation name, scope, and any initial AI context in your notes.

> **Note:** Investigations created from Insider Risk Management cases automatically include case items as data sources. Some analysis results may take time to appear depending on licensing and timing.

<validation step="Insider Risk / investigation artifacts"/>

---

## Task 5: Create a Notice Template and Capture Investigation Evidence

### Notice Template

Navigate to **Insider Risk Management** > **Notification templates** > **Create notification template**.

| Setting | Value |
|---|---|
| Template name | `Titan Journey Reminder Notice` |
| Send from | An appropriate compliance or admin sender available in the tenant |
| Subject | `Action required: review data handling guidance` |
| Message body | Explain that recent activity triggered a compliance review and direct the user to data handling guidance or refresher training |

Confirm the template appears in the notification template list. Return to your insider risk case and verify the notice template is available from the case workflow.

> **Important:** Sending a notice does not automatically resolve a case. Notice templates support workflow and user communication, but investigators must separately determine whether to continue monitoring, escalate, or resolve the case.

<validation step="Insider Risk / investigation artifacts"/>

---

## Summary

In this challenge, you reviewed Insider Risk Management readiness, created an exfiltration-focused policy, triaged an alert, analyzed user activity, opened a formal case, escalated to a Data Security Investigation, and prepared a reusable notice template. You now have the investigation artifacts needed to support remediation, compliance reporting, and the final incident narrative for the Titan Journey scenario.