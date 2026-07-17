# Decision Journal Calibration & Retro Framework

This reference outlines the quantitative and qualitative methodology for evaluating the Decision Journal (`product/decisions.md`). It ensures product managers (PMs) receive objective, feedback-driven calibration on their strategic decision-making.

---

## 1. Small-Sample Evaluation Rule (Sample Size &lt; 10)

> [!IMPORTANT]
> **Statistical Significance Safeguard:** If the number of resolved decisions in the journal is **below 10**, the agent **MUST NOT** calculate statistical metrics (such as win rates, Brier scores, or calibration percentages). Doing so over small samples is statistically invalid and creates a false sense of precision.

Instead, the Retro must generate a structured **Qualitative Calibration Report** covering:
1.  **Optimism Bias Check:** Compare the predicted metrics impact against the actual outcomes. Identify the average direction and magnitude of estimation errors (e.g., "Your predicted activation increases are consistently higher than actuals by an estimated order of magnitude").
2.  **Sunk Cost / Kill Criterion Audit:** Identify decisions where a quantitative kill criterion was met (or exceeded) but the project was shipped or kept active anyway. Explain the strategic and resource consequences of ignoring these criteria.
3.  **Leap-of-Faith Assumptions Tracker:** Highlight any implicit or explicitly logged assumptions that were proven false during delivery.

---

## 2. Large-Sample Evaluation Rule (Sample Size &gt;= 10)

When the dataset contains **>= 10 resolved decisions**, the agent calculates and displays the following quantitative calibration statistics:

### 2.1 Brier Score (Confidence Accuracy)
Measures the accuracy of probabilistic predictions.
$$\text{Brier Score} = \frac{1}{N} \sum_{t=1}^{N} (f_t - o_t)^2$$
*   Where $f_t$ is the confidence probability assigned to the success prediction (0.0 to 1.0).
*   Where $o_t$ is the actual outcome (1 if prediction was correct, 0 if incorrect).
*   **Target Score:** 0.0 is perfect accuracy; 0.25 represents random guessing; 1.0 is total miscalibration.

### 2.2 Sunk Cost Ratio (Kill Criterion Adherence)
Measures the team's discipline in killing failing bets.
$$\text{Sunk Cost Ratio} = \frac{\text{Bets kept active after meeting Kill Criteria}}{\text{Total bets that met Kill Criteria}}$$
*   **Target Score:** 0.0 (all failing bets were terminated immediately).
*   **Interpretation:** A high ratio indicates that the team uses kill criteria as "warnings" rather than hard boundaries, wasting runway on sunk costs.

### 2.3 Confidence Calibration Curve
Group predictions by confidence buckets (e.g., 50-60%, 70-80%, 90%+) and calculate the actual success rate in each bucket.
*   **Optimistic Bias:** If predictions with 90% confidence only succeed 40% of the time, the PM is overconfident.
*   **Pessimistic Bias:** If predictions with 60% confidence succeed 95% of the time, the PM is underconfident.

---

## 3. Retrospective Output Template

Every Retro output must follow this clean, structured layout:

### 🔴 🟡 🟢 Decision Journal Retro

*   **Audit Date:** YYYY-MM-DD
*   **Total Logged Decisions:** [Count]
*   **Total Resolved Decisions:** [Count]
*   **Evaluation Mode:** [Qualitative Observations / Quantitative Calibration]

#### [Section 1: Calibration Assessment]
*   *If < 10:* Qualitative assessment of optimism/pessimistic bias.
*   *If >= 10:* Brier Score, Calibration Curve table, and win/loss rates.

#### [Section 2: Kill Criteria & Sunk Cost Audit]
*   List of specific bets where kill criteria were triggered, their outcomes, and whether the team adhered to or bypassed the kill boundary.

#### [Section 3: Key Calibration Takeaways]
*   A maximum of 3 highly actionable recommendations to improve future estimation, scoping, or evidence-gathering habits.
