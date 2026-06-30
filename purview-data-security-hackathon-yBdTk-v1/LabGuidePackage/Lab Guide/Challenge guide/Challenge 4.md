# Challenge 04: DSPM & Information Barriers

**Estimated Duration:** 45 minutes

---

## Scenario

The response team has already deployed foundational labeling, DLP, and investigation controls. Your next objective is to reduce future exposure by using Microsoft Purview Data Security Posture Management (DSPM) to identify posture gaps, focus on AI-related oversharing risk, and apply a segmentation control that limits inappropriate collaboration between sensitive business groups.

---

## What You Need to Do

Review the organization's data security posture and apply a collaboration control to reduce risky paths:

1. Review DSPM posture data and protection objectives
2. Inspect AI-related recommendations and document a remediation action
3. Create two Information Barriers segments (Finance, Research)
4. Create and apply blocking policies between the segments
5. Verify enforcement and capture evidence

---

## Task 1: Access Microsoft Purview and Review DSPM Posture Data

**Portal:** [https://purview.microsoft.com](https://purview.microsoft.com)

Sign in using the lab credentials above. Navigate to **Solutions** > **DSPM**.

1. If a **Get started** or setup prompt appears, click through the setup options for **Auditing and analytics** and **Collection policies for AI**, then close the setup page.
2. In **DSPM** > **Posture**, review:
   - **Top objectives to protect sensitive data** — note the **Prevent oversharing of sensitive data** objective
   - **Data snapshot** — review available posture insights on stale/fresh data, labeling status, and exfiltration metrics
3. Navigate to **Objectives** and review the visible top objectives:
   - Prevent oversharing of sensitive data
   - Prevent exfiltration to risky destinations
   - Discover unmonitored data sources referenced by AI apps

> **Tip:** If sample data is limited, focus on the visible workflow areas Microsoft documents for DSPM: Posture, Objectives, AI observability, Activity explorer, Data risk assessments, and Remediation actions.

---

## Task 2: Inspect AI-Related Recommendations and Document a Remediation Action

1. In **DSPM** > **Objectives**, review the **Prevent data exposure in Microsoft 365 Copilot and Microsoft Copilot interactions** objective — note interaction statistics, risk indicators, and available remediation actions.

2. Navigate to **AI observability** and review the **All apps & agents** tab, noting:
   - Status, Agent ID, Risk level, Risk types, Sensitive activity trend

3. Navigate to **Discover** > **Activity explorer** and review available filters (Creation Time, Activity, Workload, Sensitive Info Types, Sensitivity Labels).

4. Navigate to **Discover** > **Data risk assessments** if results are available. Identify at least one potential oversharing concern, such as:
   - Sensitive items without labels
   - Overly broad sharing permissions
   - Sites accessible to too many users

5. Choose one remediation action recommended by DSPM (examples: restrict access by label, create an auto-labeling policy, improve a DLP policy, remove risky sharing links).

**Document in your evidence notes:**
- The recommendation name
- Why it matters to the incident scenario
- Whether you implemented it directly or recorded it as an approved next action

Capture a screenshot of the recommendation or data risk assessment.

> **Note:** Some DSPM and DSPM for AI insights depend on background data collection and can take 24 hours to several days to populate. Use visible seeded evidence if present and document the remediation decision even if live metrics are still maturing.

<validation step="DSPM / governance progress"/>

---

## Task 3: Create Information Barriers Segments

Navigate to **Solutions** > **Information Barriers** > **Segments** and create two segments.

### Segments to Create

| Segment Name | Filter Attribute | Filter Value |
|---|---|---|
| `Finance-Segment` | Department | Finance |
| `Research-Segment` | Department | Research |

**For each segment:** select **+ New segment**, set the display name, add a **Department** attribute filter with the value above, submit, and verify the **Segment created** confirmation.

After both are created, verify the **Segments** page lists both `Finance-Segment` and `Research-Segment`.

> **Important:** If the tenant already contains pre-created groups for the hackathon personas, use those groups to align your Information Barriers design to the seeded scenario.

---

## Task 4: Create and Apply Information Barriers Policies

Navigate to **Information Barriers** > **Policies** and create two blocking policies for reciprocal enforcement.

### Policies to Create

| Policy Name | Assigned Segment | Blocked Segment | Status |
|---|---|---|---|
| `Finance-Research-Block` | Finance-Segment | Research-Segment | Active (On) |
| `Research-Finance-Block` | Research-Segment | Finance-Segment | Active (On) |

**For each policy:** select **+ Create policy**, enter the name, assign the segment, set Communication and collaboration to **Blocked**, add the blocked segment, set policy status to **On**, and submit.

After both policies are created, verify both show **Active** status on the **Policies** page.

### Apply Policies

Navigate to **Information Barriers** > **Policies** > **Policy applications** and click **Apply all policies**. Monitor the **Status** and **Progress** columns — click **Refresh** if no jobs appear immediately.

> **Note:** Policy evaluation and application can take time. Capture the submitted policies and the policy application status as your primary evidence if full propagation is not immediate.

---

## Task 5: Verify Enforcement and Capture Evidence

1. In **Information Barriers** > **Policies**, confirm both policies are listed:
   - `Finance-Research-Block`
   - `Research-Finance-Block`
   - Status for both: **Active**

2. Navigate to **Policy applications** and verify the application job status is **Completed**.

Capture screenshots of the Policies page (both policies active) and the Policy applications page (completed status) for your evidence package.

<validation step="DSPM / governance progress"/>

---

## Summary

In this challenge, you reviewed Microsoft Purview DSPM posture data, investigated AI-related exposure insights, documented a remediation action, and implemented Information Barriers segmentation with reciprocal blocking policies. These actions strengthen the organization's posture by combining visibility into data risk with a concrete collaboration control that prevents future oversharing between sensitive groups.