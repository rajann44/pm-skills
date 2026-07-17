# Validation Scenario 13: Strategic Mismatch / Contradiction Warning

This scenario verifies that the agent parses active workspace files (`product/strategy.md`) and flags strategic contradictions if a requested feature does not align with the active GEM priority phase.

---

## 1. Active Workspace State

### `product/strategy.md` (Updated: 2026-07-01)
```markdown
# Product Strategy Focus

*   **Last Updated:** 2026-07-01
*   **Target Customer (ICP):** Enterprise CFOs needing automated corporate treasury reconciliations.
*   **Active Strategic Focus:** Monetization (current phase is monetization expansion; Engagement and Growth are secondary).
*   **Company Stage:** Late-stage Series B.
```

---

## 2. User Prompt
> **User Prompt:** `Write a product spec for a 'Free Viral Guest Sharing Loop' to let users easily invite external freelancers to collaborative boards.`

---

## 3. Agent Execution & Gate Evaluation

1.  **Workspace File Loading:** The agent loads `product/strategy.md` and extracts the active strategic focus: **Monetization**.
2.  **Contradiction Check:** The agent compares the request ("Free Viral Guest Sharing Loop" designed to drive signsups/Growth) with the active focus:
    *   *Requested Feature Focus:* Growth / Acquisition.
    *   *Active Workspace Focus:* Monetization.
    *   *Evaluation:* The request directly contradicts the strategy focus.
3.  **Surfacing Mismatch:** The agent halts standard output and prints the **Strategic Contradiction Detected** warning at the top of the output, requiring a formal strategic justification or a pivot in the strategy file before proceeding.

---

## 4. Agent Output Mismatch Warning

### [RESOLVED FROM WORKSPACE: product/strategy.md (Last updated: 2026-07-01)]
### [STRATEGIC CONTRADICTION DETECTED: Mismatch with focus 'Monetization' in product/strategy.md. Please provide a formal strategic justification or run 'initialize workspace state' to pivot strategy.]

# Strategic Mismatch Analysis: Free Viral Guest Sharing Loop

Your request to design a **Free Viral Guest Sharing Loop** contradicts the active strategic focus of the company:

*   **Active Strategy Focus:** Monetization (driving expansion revenue and enterprise treasury contract sizes).
*   **Proposed Feature Focus:** Growth (driving free user acquisition and freelance signups).

Early-stage freelance acquisition does not directly support the late-stage Series B monetization objectives for Enterprise CFOs. 

---

## 1. Action Options to Proceed

1.  **Strategic Justification:** If this feature is critical for Monetization (e.g. "free guest invites act as a direct trial funnel where 20% convert to paid seats within 14 days"), please provide this evidence in your prompt.
2.  **Pivot Workspace Strategy:** Run `initialize workspace state` to formally update your strategic focus in `product/strategy.md` from **Monetization** to **Growth**.
3.  **Sandbox Bypass:** Prepend your prompt with `[DRAFT-ONLY]` to lower the Context Gate and obtain the draft spec immediately (this will skip strategic alignment validation).
