# Validation Gap Log

This log tracks the rubrics, identified gaps, applied fixes, and before/after details for the validation scenarios, documenting exactly six official development gaps in accordance with the Phase 3 validation rules.

---

## 1. EVALUATION RUBRICS

### Scenario 1: Workspace PRD
1.  **Context Gate**: Fired and recorded (Strategy, Evidence, Stage).
2.  **School Selection**: Clear choice made between Cagan Outcome Brief and Shape Up Pitch; no blending.
3.  **Appetite and Boundaries**: Fixed time box and explicit out-of-scope defined.
4.  **Risk Triage**: Addressed all four risks (Value, Usability, Feasibility, Viability).
5.  **Relative Paths**: Only relative repository links are used.

### Scenario 2: 15% Activation Drop
1.  **Step-0 Check**: Verifies tracking and pipeline integrity before hypothesizing.
2.  **Step-1 Check**: Analyzes the shape of the change (Step-Change vs. Gradual Trend).
3.  **Funnel Separation**: Separates Activation, Retention, and Referral stages.
4.  **Telemetry Triangulation**: Triangulates interview findings with session logs.
5.  **Relative Paths**: Only relative repository links are used.

### Scenario 3: B2B Startup Strategy
1.  **ICP-First**: Starts with target customer segment and "who we win with first" definition.
2.  **DHM Evaluation**: Assesses Delight, Hard-to-copy, and Margin filters.
3.  **Moat Mechanism**: Details specific loop/mechanism, not just a label.
4.  **GEM Sequencing**: Ranks and justifies Growth, Engagement, Monetization based on company stage.
5.  **Relative Paths**: Only relative repository links are used.

### Scenario 4: Churn Interview Guide
1.  **Mom Test Rules**: Avoids hypothetical questions; focuses on past behavior.
2.  **No Churn Commitment Misuse**: Does not use commitment signals to validate churned users.
3.  **Sampling Bias Mitigation**: Proposes incentives and proxy populations.
4.  **Telemetry Triangulation**: Outlines session-log triangulation prior to the call.
5.  **Relative Paths**: Only relative repository links are used.

### Scenario 5: Backlog Roadmap Prioritization
1.  **Context Gate Fired**: Rejects rating impact without strategy context.
2.  **Evidence Citations**: Every feature rating cites a source or is marked `[ASSUMPTION]`.
3.  **Capacity Check**: Verifies capacity/appetite before moving tasks into "Now."
4.  **Now/Next/Later Mapping**: structured without calendar dates.
5.  **Relative Paths**: Only relative repository links are used.

### Scenario 6: Chatbot PRD Pushback
1.  **License to Say No**: Pushes back against competitor-clone request with zero evidence.
2.  **Proposes Discovery**: Suggests a lightweight validation cycle (OST/fake door) first.
3.  **Minified Draft**: Outputs the smallest useful draft, labeled **[EVIDENCE-FREE DRAFT]**.
4.  **Risk Triage**: Identifies value and viability risks of the AI chatbot.
5.  **Relative Paths**: Only relative repository links are used.

### Scenario 7: Ambiguous Routing
1.  **No Dump**: Rejects dumping a strategy or execution doc prematurely.
2.  **Diagnostic Questions**: Asks structured questions across the 4 pillars.
3.  **Isolates Problem**: Guides the user to identify the specific area of concern first.
4.  **Relative Paths**: Only relative repository links are used.

### Scenario 11: Silent Gate Resolution
1.  **Workspace File Loading**: Detects and reads `product/strategy.md` to load strategic focus, ICP, and stage.
2.  **Output Header Citation**: Prepends a header citation mapping the loaded file name and its last updated date.
3.  **Staleness Check**: Computes strategy date age vs. `2026-07-18`, appending a warning if age is > 90 days.
4.  **Strategic Focus Check**: Verifies that the requested feature is aligned with the loaded strategy focus.
5.  **Relative Paths**: Only relative repository links are used.

### Scenario 12: Decision Journal Calibration Retro
1.  **Loads Journal**: Reads `product/decisions.md` containing past decisions.
2.  **Small-Sample Rule Enforced**: If resolved decisions are < 10, disables all statistical percentages and Brier score.
3.  **Qualitative Analysis**: Evaluates optimism bias (predicted vs. actual) and sunk cost violations (ignored kill criteria).
4.  **Takeaway Tips**: Outputs 2–3 specific, actionable calibration takeaways.
5.  **Relative Paths**: Only relative repository links are used.

### Scenario 13: Strategic Mismatch / Contradiction Warning
1.  **Loads Strategy**: Reads `product/strategy.md` to find the active focus.
2.  **Mismatched Focus Detected**: Compares the request with the focus and flags a contradiction.
3.  **Surfaces Contradiction**: Outputs a Strategic Contradiction warning in the header.
4.  **Action Options**: Provides clear options to proceed (strategic justification, pivot strategy, or sandbox bypass).
5.  **Relative Paths**: Only relative repository links are used.

---

## 2. LOGGED GAPS

### Gap 1: Multi-File Routing for Prioritization was Too Ambiguous
*   **Description:** In Scenario 5, the router directed the agent to load both `strategy.md` and `execution.md` for roadmapping, but `SKILL.md` lacked instructions on *how* to combine them. Specifically, it did not state that Gibson Biddle's GEM priorities from `strategy.md` must serve as the primary weighting system for the T-shirt size "Impact" scores in `execution.md`.
*   **Fix:** Added an explicit instruction under Workflow D in `SKILL.md` forcing the agent to align T-shirt size impact ratings directly with the active GEM priority rank from the strategy context.

### Gap 2: Interview Guide Template Lacked Telemetry Context Block
*   **Description:** In Scenario 4, the Customer Interview Guide in `references/artifacts-templates.md` did not have a dedicated placeholder for telemetry logs, meaning agents running churn research would forget to triangulate behavioral session data before drafting the interview script.
*   **Fix:** Inserted a mandatory `## 0. Quantitative Telemetry Context` block at the top of the Customer Interview Guide template.

### Gap 3: PRD Template Allowed Blend "Smoothies" of Conflicting Schools (Type: Wording)
*   **Description:** In Scenario 1, the PRD template in `references/artifacts-templates.md` did not explicitly prevent blending Cagan outcome briefs with Shape Up pitches. An agent could write a document that filled out both sections, violating the anti-pattern of "framework smoothies."
*   **Fix:** Added explicit `[OR]` markdown dividers and conditional comments in `references/artifacts-templates.md` to make the choices mutually exclusive, and updated Workflow A in `SKILL.md` to require selecting one school.

### Gap 4: Input Mutation / Validation Integrity (Type: Integrity)
*   **Description:** In Scenario 5's prioritization matrix and Now/Next/Later roadmap, the feature "Stripe Billing Integration" was introduced. This represents an input mutation defect, as Stripe was not in the scenario's 8-feature request list (Slack Integration, SSO, Dark Mode, CSV Export, Mobile Push Notifications, Real-Time Collaboration, Audit Logs, Custom Dashboards).
*   **Fix:** Replaced "Stripe Billing Integration" with the original "Mobile Push Notifications" feature in `./validation/scenario-5.md`, rating it based on actual telemetry and mapping it to the Now/Next/Later roadmap.

### Gap 5: Cross-Artifact Strategy & Prioritization Contradiction (Type: Reasoning)
*   **Description:** In Scenario 3, the B2B Analytics startup strategy defined the GEM sequencing phase as Engagement (Retention) first, then Monetization, then Growth. However, in Scenario 5, the backlog prioritization context gate declared the startup's active strategy as "Monetization First," leading to prioritizing SSO and billing over engagement features. This is a direct logical contradiction between the strategic plan and the execution prioritization for the same product.
*   **Fix:** Updated Workflow D in `./product-management/SKILL.md` to mandate a strategy alignment check: the active prioritization focus (e.g., Monetization) must match the active phase of the GEM roadmap. If they differ, the prioritizer must explicitly justify the strategic pivot.

### Gap 6: Subjective Roadmap Transitions ("Roadmap Theater") (Type: Methodology)
*   **Description:** In Scenario 3's strategy, the GLEe roadmap phases (Get Big, Lead, Expand) had no quantitative exit criteria. Transitioning from "Snowflake query caching" to "warehouse index tuning" was subjective, representing a weak planning methodology.
*   **Fix:** Updated the GLEe model instructions in `./product-management/references/strategy.md` to require defining a "Phase Exit Metric" (quantitative trigger) for each roadmap horizon.

---

## 3. FIX DETAILS & DIFFS

The following fixes were implemented to resolve the logged gaps:

### Diff for Gap 1 (Prioritization & GEM Alignment)
```diff
### Workflow D: Prioritize a Backlog / Build a Roadmap
 1.  **Gather Strategy & Appetite**: Require target outcomes and team capacity before sorting.
+2.  **GEM Alignment**: Align T-shirt size impact ratings directly with the active GEM priority rank from the Strategy Context (e.g., if Monetization is rank #1, features that improve margins receive higher strategic weight than those focused on acquisition). Refer to `./references/strategy.md` for GEM details.
-2.  **Evidence Check**: For every feature, require an **Evidence Citation** (e.g., "30% of target cohort sessions dropped at X"). If none, label it as **[ASSUMPTION]**.
+3.  **Evidence Check**: For every feature, require an **Evidence Citation** (e.g., "30% of target cohort sessions dropped at X"). If none, label it as **[ASSUMPTION]**.
-3.  **Capacity Check**: Never place an initiative in "Now" without verifying team capacity and cycle appetite.
+4.  **Capacity Check**: Never place an initiative in "Now" without verifying team capacity and cycle appetite.
-4.  **Map to a Now/Next/Later roadmap using `./references/artifacts-templates.md`.
+5.  **Map to a Now/Next/Later roadmap using `./references/artifacts-templates.md`.
```

### Diff for Gap 2 (Telemetry Context Block)
```diff
 # Customer Interview Guide: [Interview Goal]
 
+## 0. Quantitative Telemetry Context (Mandatory for Churn Research)
+*   **Active Session Data Summary:** [Paste insights from actual cohort telemetry. e.g., "User logged in twice, spent 8 minutes on page X, encountered 2 errors. Refer to `./discovery.md` for triangulation steps."]
+
 ## Prep & Ground Rules
 *   Never talk about our future features or product ideas.
```

### Diff for Gap 3 (Mutually Exclusive PRD Templates)
```diff
 ### [SECTION A: Outcome Brief Style (Marty Cagan)]
+<!-- CHOOSE SECTION A OR SECTION B; DO NOT BLEND. REFER TO ./conflicts.md FOR DECISION CRITERIA -->
 *(Use if Cagan-style is selected. Focuses on outcomes and gives engineers total solution autonomy)*
...
----
+<!-- [OR] -->
 
 ### [SECTION B: Shaped Pitch Style (Shape Up)]
+<!-- CHOOSE SECTION A OR SECTION B; DO NOT BLEND. REFER TO ./conflicts.md FOR DECISION CRITERIA -->
 *(Use if Shape Up is selected. Focuses on timeboxes and boundary definition)*
```

---

## 4. CONTENT INSIGHTS

### Insight 1: Surface-Level Chatbot Value Risk Analysis (Conversational Friction)
*   **Description:** In Scenario 6, the chatbot's Value Risk was formulated as a simple "will they use it vs. standard search." This is a content-level product insight rather than a logical defect in the skill's reasoning. Typing conversational prompts has higher cognitive load and takes longer than keyboard shortcuts or clicking direct links, representing an interaction friction risk.
*   **Integration:** Added an "AI Value Risks: Conversational Friction" warning to `./product-management/references/discovery.md` explaining prompt-friction.

