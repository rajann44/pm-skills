# Validation Scenario 9: Sunk Cost Evaluation (Marketplace Feature)

This artifact represents the output of Workflow B, D, and E under the `product-management` skill, applying retention curve diagnostics and sunk-cost pivot frameworks.

---

## 1. Context Gate (Mandatory)
*   **Strategy Context / ICP:** Note-taking marketplace matching professional template creators (sellers) with note consumers (buyers).
*   **Evidence Base:** 4 months of engineering effort spent. Early beta metrics show:
    *   *Weekly Active Sellers:* Only 12% weekly active among invited sellers.
    *   *Retention Curve:* Flat retention curve at 10% after Week 3. Refer to the retention diagnostics in `../product-management/references/metrics-growth.md#2-retention-curves--pmf-diagnostics`.
*   **Stage & Constraints:** Seed stage startup with 3 months of runway remaining.

---

## 2. PMF Retention Warning & Sunk Cost Fallacy

> [!CAUTION]
> **PMF Red Flag: Flat Retention Curve**
> A flat retention curve at 10% means 90% of sellers who try the marketplace stop using it permanently. There is no Product-Market Fit. Proceeding with a full public launch will result in high churn, brand erosion, and a waste of our remaining 3 months of cash runway. We must ignore the 4 months of "sunk cost" and evaluate our options objectively.

---

## 3. strategic Pivot Options (Ship / Iterate / Kill)

We present three paths to leadership:

### Option A: Kill the Project (Recommended)
*   **Action:** Deprecate the marketplace beta, write off the 4-month build, and return the developers to optimizing the core note-taking engine (which has stable 45% retention).
*   **Decision Criterion:** Choose this if seller interviews show they cannot make meaningful revenue because buyers are unwilling to pay for notes.

### Option B: Iterate (Falsifiable Sprint)
*   **Action:** Run a single 2-week cycle to resolve the primary usability blocker: lack of automated email alerts when a buyer requests a custom template.
*   **Decision Criterion:** If a new cohort of 20 sellers shows a Week-3 retention curve that flattens above **30%**, we fund a gradual rollout. If the curve remains at 10%, we kill the marketplace immediately.

### Option C: Ship to General Availability (GA)
*   **Action:** Proceed with a public launch as requested by leadership.
*   **Warning Label:** **[HIGH-RISK LAUNCH WITHOUT RETENTION PMF]**
*   **Decision Criterion:** Only select this if the board contractually mandates a marketplace launch to secure our next funding tranche, and we explicitly accept that 90% of acquired users will churn immediately.

---

## 4. [HIGH-RISK LAUNCH WITHOUT RETENTION PMF] GA Launch Plan

If leadership forces GA launch (Option C), we must limit capital burn:
1.  **Paid Acquisition Budget:** **$0** (No paid advertising, paid social, or PR agency spend).
2.  **Marketing Scope:** Simple email announcement to our existing active SaaS customer database and a single organic post on our product blog.
3.  **Customer Support Limit:** Developers will dedicate a maximum of 4 hours per week to marketplace bug fixes.
4.  **Telemetry Alert:** Set up automatic alerts to trigger if customer retention on the core SaaS product drops by >2% due to marketplace noise.
