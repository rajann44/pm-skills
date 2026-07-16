# Validation Audit Report

This report summarizes the defect investigations, gap audit findings, and fixes applied to the `product-management` skill.

---

## 1. MANDATORY DEFECT INVESTIGATIONS

### Investigation A: Scenario 2 (Re-baselining Error)
*   **Status:** Confirmed
*   **Verbatim Defect Evidence:** 
    *   *Step-0:* "A critical tracking schema bug on iOS is responsible for a false drop in reported activation rates. This is an instrumentation failure, not a product value failure."
    *   *Step-1 (Checklist run on uncorrected numbers):* "The activation rate dropped sharply from 40% to 25% overnight on July 14th (Step-Change)... Evaluate Step-Change Cause Families: Hypothesis 1 (Technical Outage)... API error rates spiked... cloud provider outage."
*   **Root-Cause Fix Applied:**
    *   Added **Rule 2 (Re-baselining)** to the telemetry diagnostics section in [references/metrics-growth.md](../product-management/references/metrics-growth.md#1-diagnostic-step-0-instrumentation-check--re-baselining) mandating the calculation of measurement error and the subtraction of reported false drops to calculate the residual real change.
    *   Added the **Linear Checklist Execution** anti-pattern to [SKILL.md](../product-management/SKILL.md#pm-anti-patterns--rectifications) to forbid running downstream causal analyses on raw, uncorrected numbers.
*   **Diff Link:** [scenario-2.diff](./diffs/scenario-2.diff)

---

### Investigation B: Scenario 3 (Moat vs. ICP Collision)
*   **Status:** Confirmed
*   **Verbatim Defect Evidence:** 
    *   *ICP:* "Data engineering and BI trios... at mid-market Fintech companies ($50M–$200M ARR)"
    *   *Moat Claim:* "Data Loop: More queries processed → improved query cache prediction accuracy → faster response times for all users in the network."
*   **Root-Cause Fix Applied:**
    *   Added **Rule (ICP Stress-Test)** to [references/strategy.md](../product-management/references/strategy.md#2-the-dhm-model--moat-mechanisms) to explicitly require stress-testing data loops against ICP data confidentiality and regulatory constraints (e.g., PCI-DSS, SOC2).
    *   Revised [scenario-3.md](./scenario-3.md) to reject cross-company data pooling as legally and commercially impossible for Fintechs, replacing it with secure VPC-peering compliance barriers and deep metadata-mapping switching costs.
*   **Diff Link:** [scenario-3.diff](./diffs/scenario-3.diff)

---

### Investigation C: Scenario 6 (Ceremonial vs. Substantive Pushback)
*   **Status:** Confirmed
*   **Verbatim Defect Evidence:**
    *   *Ceremonial Pushback:* "Recommendation: Run a 1-Week Discovery Phase First... We recommend running a lightweight, non-functional discovery test (such as a sidebar fake-door button or customer interviews)..."
    *   *Over-designed Draft:* Outputted a multi-section document covering appetite (2 weeks), solution boundaries (breadboard), explicit out-of-bounds, and four product risks.
*   **Root-Cause Fix Applied:**
    *   Upgraded the **License to Say No** guidelines in [SKILL.md](../product-management/SKILL.md#license-to-say-no) to require:
        1. Naming specific unvalidated assumptions (Value, Usability, Feasibility, Viability).
        2. Proposing a 1-week discovery plan with quantitative, falsifiable **kill criteria**.
        3. A genuinely minified draft restricted to under 10 lines of core logic.
        4. A positive decision framework for the CEO.
*   **Diff Link:** [scenario-6.diff](./diffs/scenario-6.diff)

---

### Investigation D: Scenario 1/3/5 (The Self-Served Evidence Problem)
*   **Status:** Confirmed
*   **Verbatim Defect Evidence:**
    *   *Context Gate:* "Evidence Base: Citing User Interview Report Doc L3 showing 8 out of 10 users share login credentials..."
    *   *Appetite:* "6 weeks (Big Batch cycle)."
*   **Root-Cause Fix Applied:**
    *   Implemented the **Minimum Evidence Weight Rule** under the Context Gate in [SKILL.md](../product-management/SKILL.md#the-context-gate). A 6-week Big Batch bet now requires observations across at least 5 independent interviews or telemetry showing >15% user impact; a single user interview or support ticket (or a report showing <5 interviews) can only justify a 2-week cycle or discovery spike.
    *   Revised [scenario-1.md](./scenario-1.md) to evaluate that the User Interview Report L3 contains only 3 independent interviews, resulting in scaling down the appetite to a 2-week Small Batch folder-sharing link and deprecating real-time database editing.
*   **Diff Link:** [scenario-1.diff](./diffs/scenario-1.diff)

---

## 2. AUDITED GAPS & TYPES

| Gap ID | Name / Description | Defect Type | Status |
| :--- | :--- | :--- | :--- |
| **Gap 1** | Multi-File routing for prioritization GEM alignment. | Reasoning | Fixed |
| **Gap 2** | Customer interview template lacked telemetry context header. | Methodology | Fixed |
| **Gap 3** | PRD template allowed framework smoothies. | Wording | Fixed |
| **Gap 4** | Input mutation in Scenario 5 feature list (Stripe billing migration). | Integrity | Fixed |
| **Gap 5** | Strategy vs. Prioritization cross-artifact contradiction. | Reasoning | Fixed |
| **Gap 6** | Subjective roadmap transitions in GLEe model. | Methodology | Fixed |
| **Gap 7** | Surface-level Value Risk analysis for productivity AI chatbot. | Spine | Fixed |

---

## 3. THREE WEAKEST ASPECTS OF THE SKILL (Remaining)

1.  **Lack of Go-To-Market (GTM) and Pricing Mechanics:**
    While the skill is highly detailed on product discovery (Torres, Fitzpatrick) and delivery cycles (Singer, Cagan), it contains virtually zero frameworks for GTM execution, sales enablement, or monetization packaging (e.g. usage-based pricing grids, packaging tier structures, or free-to-paid conversion triggers). It assumes monetization strategy is pre-set.
2.  **No Diagnostic Framework for Technical Architecture Debt:**
    The skill fails to address technical PM trade-offs like microservices migration, API deprecation strategies, database sharding, or technical debt allocation. A technical PM seeking guidance on how to prioritize clean-up work vs. feature delivery will find only general OKR and RICE discussions.
3.  **B2B SaaS Bias:**
    The frameworks (such as the Mom Test, Shape Up, Cagan briefs, and GEM sequencing) are heavily optimized for B2B SaaS. The skill does not support complex consumer growth loops, virality coefficients, marketplace liquidity levers (e.g., matching engines), or hardware product lifecycle constraints.
