# Validation Scenario 4: Week 2 Churn Interview Guide

This artifact represents the output of Workflow C under the `product-management` skill, applying the Mom Test guidelines and churn sampling-bias mitigations.

---

## 0. Quantitative Telemetry Context (Mandatory)
*   **Active Session Data Summary:** Telemetry cohort analysis shows that users who churn in Week 2 logged in exactly once (on Day 1) for less than 5 minutes. 85% of these users clicked "Add Integrations" but failed to connect any data sources. Zero events were logged for `data_connected_success`. Refer to the telemetry triangulation guidelines in `../product-management/references/discovery.md#5-churn-interview-limits--telemetry-triangulation`.

---

## 1. Interview Prep & Sampling Bias Mitigation
*   **Sampling Bias Handling:** Churned users who agree to speak with us are outliers. To mitigate this:
    1.  We offer a high-value incentive ($100 Amazon gift card) for a 15-minute call.
    2.  We study a "proxy population": active users who signed up last week but have shown a precipitous drop in daily sessions.
    3.  We triangulate these interview findings with our database event logs.
*   **Commitment Signal Policy:** We **do not** use commitment signals (like pre-orders or intros) to validate interest. These users have already churned and want to disengage. Seeking further commitments will bias their answers or cause them to abort the call.

---

## 2. Interview Script (Mom Test Compliant)

### Introduction (2 mins)
"Thanks for jumping on the call. We noticed you recently signed up for our analytics tool and then stopped using it. I'm not here to sell you anything or convince you to return. I just want to understand your real workflow to improve the product. There are no wrong answers."

### Context & past workflows (5 mins)
*   "Walk me through the day you decided to sign up. What was happening at work? What problem were you trying to solve?"
*   "How do you currently track those metrics? What tools do you use?"

### Main Narrative (8 mins)
*   "When you first logged into our app, what was the first action you took?"
*   "I saw in our logs that you opened the 'Add Integrations' page. Walk me through what happened next. What data source were you trying to connect?"
*   "What came up during that setup process? Did you run into any error messages or layout issues?"
*   "Did you have to seek approval from your IT or security team to connect that data? How does your company handle those approvals?"
*   "After that first session, did you try to log back in? Why or why not?"

### Closing
"Thank you for sharing your experience. Your feedback on the integration flow is extremely helpful."
