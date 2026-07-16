# Product Metrics & Growth Reference

This document provides detailed guidelines for selecting metrics, designing growth loops, analyzing retention cohorts, and establishing leading proxy metrics.

---

## TABLE OF CONTENTS
- [1. Diagnostic Step-0: Instrumentation Check](#1-diagnostic-step-0-instrumentation-check)
- [2. Diagnostic Step-1: Shape Analysis](#2-diagnostic-step-1-shape-analysis)
- [3. Funnel Separation: Pirate Metrics (AARRR)](#3-funnel-separation-pirate-metrics-aarrr)
- [4. North Star Metric Selection](#4-north-star-metric-selection)
- [5. Growth Loops vs. Funnels](#5-growth-loops-vs-funnels)
- [6. Retention Curves & Cohort Analysis](#6-retention-curves--cohort-analysis)
- [7. Proxy Metrics](#7-proxy-metrics)

---

## 1. Diagnostic Step-0: Instrumentation Check & Re-baselining

Before formulating hypotheses or taking action on any product metric change (e.g., "activation dropped 15%"), you **must** perform a sanity check on your telemetry tracking and re-baseline if a bug is identified.
*   **Rule 1:** Never trust a metric change without checking the data pipeline.
*   **Rule 2 (Re-baselining):** If an instrumentation bug is found, you **must** calculate the measurement error:
    1.  *Quantify the Error:* Identify what percentage of the drop is due to the logging failure (e.g., if iOS users represent 66% of the traffic, and iOS logging was completely broken, the logging bug explains a `15% * 0.66 = 10%` reported drop).
    2.  *Calculate the Residual:* Subtract the quantified tracking error from the reported change to calculate the **residual real change**: `Reported Drop (15%) - Measurement Error (10%) = Residual Real Drop (5%)`.
    3.  *Pivot Decision:* If the residual is zero, halt the investigation and resolve the tracking bug. If the residual is non-zero, proceed to Step-1 using *only* the residual change (5%) for shape analysis and causal hypotheses.
*   **Rule 3 (Decomposition & Uncertainty):** Metric decompositions must explicitly state their quantification method (e.g., comparing affected cohort counts against pre-release baselines or stable control groups) and acknowledge uncertainty (error bands, confidence intervals, or behavioral interaction effects). If a diagnostic attribution changes between analyses (e.g., a technical outage is ruled out in favor of an acquisition mix shift), the PM must document the evidence for that transition rather than silently overwriting the history.
*   **Checklist:**
    1.  *Schema Changes:* Has the event definition or trigger point changed in the code repository?
    2.  *Logging Outage:* Are events failing to log on specific platforms (e.g., did an iOS app update break Segment/Amplitude SDK initialization)?
    3.  *Telemetry Latency:* Is there a delay in the database replication or processing pipeline?
    4.  *Double Logging:* Are events being sent twice due to a frontend loop?

---

## 2. Diagnostic Step-1: Shape Analysis

Once instrumentation is verified, plot the metric over time to analyze the **shape** of the change. The shape directs you toward distinct cause families:
*   **Step-Change (Sudden Drop/Spike):** The metric drops precipitously overnight.
    *   *Cause Families:* Technical deployment outage, third-party API failure, sudden marketing campaign launch/stop, seasonal holiday (e.g., Christmas Day), or tracking bug.
*   **Gradual Trend (Slow Decay/Growth):** The metric degrades slowly over weeks or months.
    *   *Cause Families:* Shifting user cohorts, change in acquisition traffic mix (e.g., higher volume of lower-intent paid ads traffic), slow competitive erosion, or onboarding drift.

---

## 3. Funnel Separation: Pirate Metrics (AARRR)

*   **Definition:** A linear product funnel framework that maps the user journey.
*   **v2 Hardening Rule (Funnel Separation):** Keep Activation, Retention, and Referral behaviors in separate, non-overlapping funnel stages. Mixing them (e.g., treating "invited a colleague" as both activation and referral) makes diagnostic analysis impossible.
    1.  **Acquisition:** Visitor lands and signs up.
    2.  **Activation:** The user experiences the core value ("Aha! moment") for the first time within a fixed window (e.g., created 1st document in 24 hours).
    3.  **Retention:** The user continues to actively use the product over subsequent cycles (e.g., logs in 3+ days in week 2).
    4.  **Referral:** The user invites others, expanding the user base (e.g., sent team invitation).
    5.  **Revenue:** The user converts to a paid subscription.
*   **Worked Example:** A SaaS tool sets distinct telemetry hooks: `event: signup` (Acquisition) -> `event: first_project_created` (Activation) -> `event: session_start_week_2` (Retention) -> `event: invite_sent` (Referral).
*   **Source URL:** [mindtheproduct.com](https://www.mindtheproduct.com)

---

## 4. North Star Metric Selection

*   **Definition:** The single key metric that best captures the core value your product delivers to its customers, serving as the primary driver for long-term sustainable business growth.
*   **When to use:** Use this when defining a product's high-level strategy to align all product teams.
*   **When NOT to use:** Do not use revenue, stock price, or profit as a North Star metric (these are lagging financial indicators).
*   **Worked Example:** Airbnb uses **Nights Booked** rather than revenue. This captures value for guests and hosts, and directly drives Airbnb's business growth.
*   **Source URL:** [lennysnewsletter.com/p/choosing-your-north-star-metric](https://www.lennysnewsletter.com)

---

## 5. Growth Loops vs. Funnels

*   **Definition:** A growth loop is a closed-loop system where the output of one step is directly reinvested as an input to the next step, creating a self-reinforcing flywheel.
*   **When to use:** Use this when designing a product's sustainable, long-term acquisition and retention engine.
*   **Worked Example:** Pinterest's content loop. *Input:* User signs up and searches. *Action:* User saves a pin to their board. *Output:* Search engines index this board. *Reinvestment:* New users discover Pinterest via search, leading to new sign-ups.
*   **Source URL:** [reforge.com/blog/growth-loops](https://reforge.com/blog/)

---

## 6. Retention Curves & Cohort Analysis

*   **Definition:** A cohort analysis groups users by their signup date and tracks active usage over time. The resulting retention curve plots the percentage of users returning at Day/Week/Month X. A flattening curve parallel to the x-axis indicates a stable user base, serving as the primary metric signal of Product-Market Fit (PMF).
*   **When to use:** Use this to measure product-market fit, analyze onboarding health, and diagnose long-term user retention.
*   **Worked Example:** A B2B note-taking app measures weekly retention. If the retention curve drops from 100% to 20% by Week 4 but then remains flat at 20% through Week 12, it proves PMF for a specific 20% segment of users.
*   **Source URL:** [reforge.com/blog](https://reforge.com/blog/)

---

## 7. Proxy Metrics

*   **Definition:** A measurable, short-term leading indicator that product teams can directly influence, which is mathematically or behaviorally correlated to a lagging, long-term business outcome (like churn or customer lifetime value).
*   **When to use:** Use this to give product teams actionable, short-term targets for their cycles.
*   **Worked Example:** Netflix personalization proxy metric. *Lagging Metric:* Monthly subscriber retention. *Hypothesis:* Users who configure their preference queue early are less likely to churn. *Proxy Metric:* The percentage of members who add at least 3 titles to their Queue within their first 30 days.
*   **Source URL:** [gibsonbiddle.com/proxy-metrics](https://www.gibsonbiddle.com)
