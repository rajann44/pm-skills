# Validation Spot-Check Report

This document reports the findings, verdicts, and applied fixes for the release spot-checks.

---

## Spot-Check 1: Scenario 2 (15% = 9% + 6% Decomposition)

### 1. Quantification Method
*   **Question:** HOW was the 9% telemetry error quantified?
*   **Verdict:** **FAIL** (Originally unstated method)
*   **Quoted Evidence (Original):** *"iOS users represent exactly 60% of our daily signup volume. The complete logging outage on iOS accounts for a false drop of `15% * 0.60 = 9%`..."*
*   **Fix Applied:** Updated [scenario-2.md](./scenario-2.md) to explicitly state the verification method: comparing the active iOS cohort event counts against the pre-release v2.4.1 baseline (where activation was stable at 40%), while validating against stable Web and Android control cohorts which showed zero baseline drop.

### 2. Acknowledge Decomposition Uncertainty
*   **Question:** Does the artifact acknowledge uncertainty, or present 9+6=15 as exact arithmetic?
*   **Verdict:** **FAIL** (Originally exact arithmetic)
*   **Quoted Evidence (Original):** *"Reported Drop (15%) - Telemetry Error (9%) = Residual Real Drop (6%)"*
*   **Fix Applied:** Updated [scenario-2.md](./scenario-2.md) to introduce a +/-2% uncertainty band due to interaction effects. Crashing iOS launch builds likely caused a portion of real iOS users to churn completely on Day 1, making the actual tracking error between 7% and 11% (residual real drop range: 4% to 8%).

### 3. Attribution Change Explanation
*   **Question:** Does the artifact explain why the attribution changed (cloud outage -> Google Ads), or did the story silently mutate?
*   **Verdict:** **FAIL** (Originally silently mutated)
*   **Quoted Evidence (Original):** The cloud outage spike from the first draft was replaced silently with Google Ads gradual mix shift.
*   **Fix Applied:** Updated [scenario-2.md](./scenario-2.md) to add Section 2.2 ("Attribution Transition Explanation"), documenting that the July 14th connection spike was ruled out because the re-baselined Web/Android metric trend showed a gradual 4-week decline rather than an overnight step-change.
*   **Root Cause Fix:** Added **Rule 3 (Decomposition & Uncertainty)** to [references/metrics-growth.md](../product-management/references/metrics-growth.md#1-diagnostic-step-0-instrumentation-check--re-baselining) to mandate quantification methods, error bands, and transition explanations.

---

## Spot-Check 2: Scenario 6 (8% Fake-Door CTR Kill Criterion)

### 1. Anchoring of Thresholds
*   **Question:** Is the 8% threshold anchored, or is it an unanchored number?
*   **Verdict:** **FAIL** (Originally unanchored)
*   **Quoted Evidence (Original):** *"KILL the project if CTR is < 8% (indicates lack of user interest)."*
*   **Fix Applied:** Updated [scenario-6.md](./scenario-6.md) to anchor the 8% threshold to 50% of the historical median entry-point CTR of 16% for other new features, representing the minimum interest required to cover LLM server and operations costs.
*   **Root Cause Fix:** Upgraded Falsifiable Kill Criteria in [SKILL.md](../product-management/SKILL.md#license-to-say-no) to require that every quantitative kill criterion states its anchor or is labeled an assumption with a stated revisit trigger.

---

## Spot-Check 3: Gap 7 Reclassification

### 1. Classification Integrity
*   **Question:** Is Gap 7 a reasoning defect or a content insight?
*   **Verdict:** **CONTENT INSIGHT** (Reclassified)
*   **Action Taken:** Moved Gap 7 from the official gaps list to a new `## 4. CONTENT INSIGHTS` section in [gap-log.md](./gap-log.md), and corrected the official gap count in `gap-log.md` from 7 to 6.
