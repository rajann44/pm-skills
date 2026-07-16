# Validation Scenario 2: 15% Activation Rate Drop Investigation

This artifact represents the output of Workflow E under the `product-management` skill, applying Step-0 (Instrumentation & Re-baselining) and Step-1 (Shape Analysis).

---

## 1. Diagnostic Step-0: Instrumentation Check & Re-baselining
Before investigating product or system hypotheses, we verify telemetry pipeline integrity, quantify measurement error, and re-baseline. Refer to the metrics framework in `../product-management/references/metrics-growth.md#1-diagnostic-step-0-instrumentation-check--re-baselining`.

1.  **Check Telemetry Logs:**
    *   *Action:* Audit Segment/Amplitude SDK initialization logs.
    *   *Result:* iOS SDK initialization crashed on app launch starting July 12th due to a dependency conflict in iOS release v2.4.1. Android and Web SDKs are logging normally.
2.  **Quantify the Measurement Error (Methodology):**
    *   *Method:* We compare the active iOS cohort event counts against the pre-release v2.4.1 baseline. The baseline iOS activation rate was stable at 40%. Post-release, reported iOS note creation events dropped to zero. In contrast, Web and Android controls remained stable.
    *   *Calculation:* Since iOS users represent exactly 60% of our daily signup volume, a complete tracking outage on iOS accounts for a false reported drop of `15% * 0.60 = 9%` in our overall reported activation rate.
3.  **Acknowledge Uncertainty and Interaction Effects:**
    *   *Error Bands:* While the direct logging failure accounts for a 9% reported drop, we acknowledge a +/-2% uncertainty band due to interaction effects. Specifically, the iOS app crashes on launch likely caused a portion of real iOS users to churn completely on Day 1. This means the actual tracking error is between 7% and 11%.
4.  **Calculate the Residual Real Change:**
    *   *Re-baselining formula:* `Reported Drop (15%) - Telemetry Error (9%) = Residual Real Drop (6%)` (with a residual range of 4% to 8%).
    *   *Pivot Decision:* Because the residual real drop is non-zero, we halt the iOS tracking bug investigation as the sole cause and proceed to Step-1 to diagnose the remaining 6% real drop using *only* Web and Android data.

---

## 2. Diagnostic Step-1: Shape Analysis & Hypotheses
We perform shape analysis on the re-baselined 6% residual drop using Web and Android cohort data.

1.  **Plot the Residual Metric Trend:**
    *   *Action:* Chart Web and Android activation rates over the last 30 days.
    *   *Result:* The activation rate on Web and Android has declined slowly and steadily from 42% to 36% over the past 4 weeks (Gradual Trend). It is not a sudden Step-Change.
2.  **Attribution Transition Explanation (Why the Cause Changed):**
    *   *Initial Analysis Round:* The team initially blamed the 15% drop on a database server connection spike on July 14th (a Step-Change). 
    *   *Pivot Explanation:* After re-baselining and isolating Web/Android data, we observed the drop was actually a gradual 4-week trend (from 42% to 36%). This rules out the July 14th database spike (which was a 1-day outage that had already been resolved). We pivot our focus to acquisition cohort changes.
3.  **Evaluate Gradual Trend Cause Families:**
    *   *Hypothesis 1 (Acquisition Mix Shift):* A change in signup traffic source. Check signup attribution logs for the past 4 weeks.
        *   *Telemetry Evidence:* Google Search Ads traffic (lower-intent search keywords) increased by 35% on Web, while organic referrals remained flat.
    *   *Hypothesis 2 (Onboarding Drift):* Increased user onboarding friction.
        *   *Telemetry Evidence:* Onboarding completion rates remained flat at 78% for Web/Android.
4.  **Friction Point Isolation (Telemetry Triangulation):**
    *   *Action:* Review query logs and session parameters for the paid acquisition cohort.
    *   *Result:* Paid ads traffic has a 90% drop-off rate on the `create_first_dashboard` aha milestone. These users are searching for general templates and leave when prompted to write SQL queries.

## Action Plan
1.  **Resolve Telemetry Outage:** Roll back the iOS v2.4.1 SDK package conflict to restore correct iOS activation reporting.
2.  **Optimize Paid Acquisition:** Align marketing keywords in Google Ads to target senior data analysts (ICP) rather than general business users, halting the gradual drift in non-activated signups.
