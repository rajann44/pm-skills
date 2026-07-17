# Validation Scenario 12: Decision Journal Calibration Retro

This scenario verifies the execution of the Retro workflow (`review my decision journal`) on a small sample of resolved decisions (count < 10). It ensures the agent evaluates decisions qualitatively without calculating statistically invalid percentages or Brier scores.

---

## 1. Local Journal State

### `product/decisions.md`
```markdown
# Product Decision Journal

*   **2026-04-12 | PRD | Stripe Invoice Customization**
    *   *Predicted Outcome:* 45% reduction in invoice disputes within 30 days.
    *   *Kill Criterion:* Disputed invoice rate increases or stays flat after 14 days of beta.
    *   *Confidence:* 85%
    *   *Status:* Resolved (Actual outcome: Dispute rate fell by 40%. Prediction Successful).

*   **2026-05-01 | PRD | AI Auto-Categorize Invoices**
    *   *Predicted Outcome:* 30% increase in weekly active merchants utilizing tags.
    *   *Kill Criterion:* Tag usage rate is below 12% after 14 days of beta.
    *   *Confidence:* 90%
    *   *Status:* Resolved (Actual outcome: Tag usage was 6% on Day 14. Bet met kill criterion but project was kept active for 4 additional weeks. Prediction Failed).

*   **2026-05-20 | Prioritization | Custom Email Alerts**
    *   *Predicted Outcome:* 20% click-through rate (CTR) on billing summary emails.
    *   *Kill Criterion:* CTR falls below 8% after 7 days.
    *   *Confidence:* 70%
    *   *Status:* Resolved (Actual outcome: Actual CTR was 4.5%. Project killed on Day 7. Prediction Failed).
```

---

## 2. User Prompt
> **User Prompt:** `review my decision journal`

---

## 3. Agent Execution & Retro Calibration

1.  **Read Journal:** Loads `product/decisions.md` and parses the entries.
2.  **Determine Sample Size:** Counts the resolved decisions. Total resolved = 3.
3.  **Apply Small-Sample Rule:** Since 3 is < 10, the agent disables Brier Score, sunk cost percentages, and win rate statistics.
4.  **Qualitative Analysis:**
    *   *Optimism Bias:* Reviews estimated impacts (45%, 30%, 20%) vs. actuals (40%, 6%, 4.5%). Identifies a pattern of overestimating feature impact.
    *   *Sunk Cost Audit:* Flags the "AI Auto-Categorize" decision where tag usage was 6% (failing the 12% kill threshold), but the project was kept active anyway for 4 weeks.
5.  **Output Formatting:** Prepend mock macOS Terminal controls.

---

## 4. Agent Output Retro Report

### 🔴 🟡 🟢 Decision Journal Retro

*   **Audit Date:** 2026-07-18
*   **Total Logged Decisions:** 3
*   **Total Resolved Decisions:** 3
*   **Evaluation Mode:** Qualitative Observations (Sample size < 10 resolved decisions)

#### 1. Calibration Assessment (Optimism Bias Audit)
With a sample size of 3 resolved decisions, we are utilizing qualitative observation rather than statistical Brier scores. 
*   **Observation:** Your predictions show a consistent **Optimism Bias**. While your Stripe Invoice Customization bet was highly accurate (estimating 45% reduction vs. 40% actual), your other two predictions fell significantly short of their targets (estimating 30% and 20% vs. actuals of 6% and 4.5%). 
*   **Calibration Hint:** You appear to set confidence ratings (90% and 70%) based on enthusiasm rather than evidence base, leading to high-confidence failures.

#### 2. Kill Criteria & Sunk Cost Audit
*   **Warning (Sunk Cost Boundary Violation):** In the **AI Auto-Categorize Invoices** bet, the tag usage rate on Day 14 was 6%, failing the 12% kill threshold. However, the project was kept active for 4 additional weeks. This represents a significant sunk cost violation. When a kill criterion is triggered, the project must either be killed immediately or paused for a formal strategic pivot.

#### 3. Key Calibration Takeaways
1.  **Enforce Sunk Cost Boundaries:** Do not treat your own kill criteria as flexible guides. If a beta fails its threshold, kill it to protect team runway.
2.  **Discount Confidence Scores:** For future cycles, if the evidence weight is small-batch (1–4 interviews), cap your maximum decision confidence probability at 70%.
