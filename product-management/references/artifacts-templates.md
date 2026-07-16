# Product Management Templates Reference

This document provides ready-to-fill, structured markdown templates for standard product management documents and updates.

---

## TABLE OF CONTENTS
- [1. PRD / Pitch Template](#1-prd--pitch-template)
- [2. Product One-Pager Template](#2-product-one-pager-template)
- [3. Product Strategy Document](#3-product-strategy-document)
- [4. Opportunity Solution Tree (OST) Template](#4-opportunity-solution-tree-ost-template)
- [5. Customer Interview Guide](#5-customer-interview-guide)
- [6. Product Launch Checklist](#6-product-launch-checklist)
- [7. Stakeholder Update Format](#7-stakeholder-update-format)

---

## 1. PRD / Pitch Template

```markdown
# Product Brief / Pitch: [Feature Name]

## 1. Context Gate (Mandatory)
*   **Strategy Context / ICP:** [Target customer segment. How does this align with current strategy? e.g., SMB-first, retention focus]
*   **Evidence Base:** [Cite specific telemetry, customer interviews, or quantitative reports. e.g., Citing User Interview Report Doc X]
*   **Stage & Constraints:** [Company stage, team capacity, and appetite. e.g., early-stage startup, 1 team, 6-week appetite]

## 2. School Selection & Justification
*   **Selected School:** [Cagan-style Outcome Brief / Shape Up Pitch]
*   **Justification:** [Why choose this? e.g., "Shape Up selected because we have a fixed 6-week appetite and need to control scope." Refer to `./conflicts.md` for criteria.]

---

### [SECTION A: Outcome Brief Style (Marty Cagan)]
<!-- CHOOSE SECTION A OR SECTION B; DO NOT BLEND. REFER TO ./conflicts.md FOR DECISION CRITERIA -->
*(Use if Cagan-style is selected. Focuses on outcomes and gives engineers total solution autonomy)*
*   **Problem Statement:** [What user problem are we solving?]
*   **Business Opportunity / OKR:** [What business outcome is this tied to? e.g., increase Week-2 retention by 5%]
*   **Risks & Validation Tests:**
    *   *Value Risk:* [How do we test if they want it?]
    *   *Usability Risk:* [How do we test if they can use it?]
    *   *Feasibility Risk:* [What engineering spikes are needed?]
    *   *Viability Risk:* [Are there legal, support, or billing implications?]

<!-- [OR] -->

### [SECTION B: Shaped Pitch Style (Shape Up)]
<!-- CHOOSE SECTION A OR SECTION B; DO NOT BLEND. REFER TO ./conflicts.md FOR DECISION CRITERIA -->
*(Use if Shape Up is selected. Focuses on timeboxes and boundary definition)*
*   **Appetite:** [e.g., 6 weeks or 2 weeks]
*   **Solution Boundaries (Breadboard):**
    *   `[Page A] -> (Action) -> [Page B]`
*   **UI Boundaries (Fat Marker Sketch Description):**
    *   [Describe high-level layout constraints. e.g., "A split pane, templates on left, preview on right. No custom drag-and-drop."]
*   **Explicit Out of Bounds (No-Gos):**
    *   [What will we NOT build in this cycle? e.g., No multi-currency billing in Phase 1.]
```

---

## 2. Product One-Pager Template

```markdown
# Product One-Pager: [Project Title]

*   **Owner:** [Your Name]
*   **Status:** [Draft / Under Review / Approved]
*   **Date:** [YYYY-MM-DD]

### 1. Context Gate
*   **Strategy Context / ICP:** [Define ICP]
*   **Evidence Base:** [Cite data or discovery]
*   **Stage & Constraints:** [Define stage and appetite]

### 2. The Opportunity (Why)
[What is the customer problem and why does it matter to our business flywheel? Connect this to the North Star Metric.]

### 3. The Proposal (What)
[A high-level overview of the proposed solution. Focus on the core mechanics, keeping descriptions abstract enough to allow developer design freedom.]

### 4. Target Outcomes (Success)
*   **Primary Metric:** [e.g., Week-1 retention rate increases from 12% to 18%]
*   **Secondary Metric:** [e.g., Number of workspaces created per week]

### 5. Boundaries & Constraints
*   **Appetite:** [e.g., 6-week cycle]
*   **Key Out of Scope:** [e.g., No mobile app support in Phase 1]
```

---

## 3. Product Strategy Document

```markdown
# Product Strategy: [Product Line/Company Name]

## 1. Strategy Context & ICP
*   **Target Segment / ICP:** [Who is the primary customer profile we must win with first?]
*   **Segment Constraints:** [What are their core pain points, budgets, and current alternatives?]

## 2. Product Vision
[The inspiring 5-10 year state of the product. What does the world look like when this is fully realized?]

## 3. Strategic Pillars (DHM Framework)
*   **Delight:** [How do we solve customer pain points better than anyone else?]
*   **Hard-to-copy (Moat Mechanisms):**
    *   *Moat Claim:* [e.g., Network Effects / High Switching Costs / Data Loop]
    *   *Moat Mechanism:* [Explain exactly how this moat strengthens as user volume scales. Avoid raw labeling.]
*   **Margin:** [How does this strategy generate profit or reduce business costs?]

## 4. Roadmap Sequencing (GLEe Model)
*   **Phase 1: Get Big On:** [Focus on the beachhead market. What is the core offering?]
*   **Phase 2: Lead In:** [How do we establish market dominance and build defensibility?]
*   **Phase 3: Expand Into:** [Where do we expand next? Adjacent products or monetization layers?]

## 5. Current Priority Rank (GEM Model)
*   **Rank:** 1. [Growth / Engagement / Monetization] | 2. [Growth / Engagement / Monetization] | 3. [Growth / Engagement / Monetization]
*   **Justification:** [Explain the priority sequencing based on company stage and cash runway. Refer to `./strategy.md` for guidelines.]
```

---

## 4. Opportunity Solution Tree (OST) Template

```markdown
# Opportunity Solution Tree: [Target Business Outcome]

## Target Outcome
*   **Metric:** [e.g., Reduce Day-7 churn by 10%]

## Opportunities (Validated Pain Points)
*   **Opportunity A:** [e.g., "I forget to use the app after the first day"]
    *   *Evidence:* [e.g., 60% of Day-1 drop-offs never log in a second time]
*   **Opportunity B:** [e.g., "I don't understand how to set up my profile"]
    *   *Evidence:* [e.g., 40% of drop-offs fail to complete the 3-step setup wizard]

## Solutions
*   *For Opportunity A:*
    *   **Solution A1:** Daily digest email summaries.
    *   **Solution A2:** Push notifications for milestone completions.
*   *For Opportunity B:*
    *   **Solution B1:** Interactive video tutorial on first login.
    *   **Solution B2:** Automated profile template pre-fills.

## Experiments
*   *For Solution A2 (Push notifications):*
    *   **Experiment A2.1:** Fake-door opt-in screen to measure CTR.
    *   **Experiment A2.2:** Manual email campaign matching the push style to check open rates.
```

---

## 5. Customer Interview Guide

```markdown
# Customer Interview Guide: [Interview Goal]

## 0. Quantitative Telemetry Context (Mandatory for Churn Research)
*   **Active Session Data Summary:** [Paste insights from actual cohort telemetry. e.g., "User logged in twice, spent 8 minutes on page X, encountered 2 errors. Refer to `./discovery.md` for triangulation steps."]

## Prep & Ground Rules
*   Never talk about our future features or product ideas.
*   Keep the user talking about their past actions and real experiences.
*   Dig into specifics: "When was the last time you..." and "How did you resolve that?"
*   **Sampling Bias Mitigation:** [Explain how you recruited this cohort and how you are triangulating their feedback with telemetry data. Refer to `./discovery.md` for details.]

## Introduction (3 mins)
*   "We are trying to understand how teams manage [problem area]. I'm not here to sell anything; I just want to hear about your actual workflow. There are no right or wrong answers."

## Warm-up / Context (5 mins)
*   "What is your role at [Company]? How much of your day is spent on [general activity]?"

## Main Narrative / Past Behavior (20 mins)
*   "Walk me through the last time you had to [perform core task]. What happened first?"
*   "What was the most frustrating part of that process? Why?"
*   "How did you solve that frustration? What did you use to fix it?"
*   "How much did that solution cost? How long did it take to set up?"

## Securing Commitment (5 mins)
*(Use for pre-sale discovery only. Do not rely on these signals for churn interviews)*
*   "You mentioned that [specific problem] is a major issue for your team. We are looking for beta testers to try a prototype next week. It will require a 30-minute feedback session. Would you be open to introducing me to your team lead to set that up?"
*   [Record Time/Reputation/Money commitment signals]
```

---

## 6. Product Launch Checklist

```markdown
# Product Launch Checklist: [Feature Name]

## 1. Readiness Gates
- [ ] Code complete, reviewed, and merged to main.
- [ ] Usability testing completed on staging (no critical UI bugs).
- [ ] Legal and privacy sign-off (GDPR / data policy compliant).
- [ ] Billing & subscription engine updated (if monetized).

## 2. Analytics & Tracking
- [ ] Event instrumentation verified on staging (clicks, views, conversions). Refer to `./metrics-growth.md` for Step-0 criteria.
- [ ] Proxy metric dashboard set up in analytics tool.
- [ ] Churn/retention cohorts set up for the launch day.

## 3. Go-to-Market (GTM)
- [ ] Internal documentation updated for Customer Support teams.
- [ ] Sales enablement briefing completed (B2B).
- [ ] Marketing/Email campaign assets scheduled.
- [ ] In-app onboarding tutorials enabled.

## 4. Rollout Schedule
- [ ] Day 1: Internal team alpha rollout (100% internal).
- [ ] Day 3: 5% beta rollout to target cohort.
- [ ] Day 7: 25% rollout, monitor performance and crash rates.
- [ ] Day 10: 100% general availability.
```

---

## 7. Now/Next/Later Roadmap Template

```markdown
# Now/Next/Later Roadmap: [Product/Team Name]

## 1. Current Capacity & Appetite
*   **Team Capacity:** [e.g., 2 engineers, 1 designer]
*   **Appetite Window:** [e.g., 6-week cycles]

## 2. Roadmap

| Time Horizon | Initiative / Customer Opportunity | Target Outcome OKR | Evidence Citation |
| :--- | :--- | :--- | :--- |
| **NOW** (Active Dev) | [e.g., Stripe billing migration to resolve card failures] | [e.g., Reduce checkout drop-off by 10%] | [Citing Telemetry report Q2 showing 15% billing card failure rate] |
| **NEXT** (Discovery) | [e.g., Interactive dashboard creator for report building] | [e.g., Increase report sharing activity by 20%] | [Citing user interviews showing 7/10 clients struggle with sharing] |
| **LATER** (Themes) | [e.g., Multi-currency localization support] | [e.g., Expand addressable market in EU] | **[ASSUMPTION]** (No discovery done yet) |
```

---

## 8. Stakeholder Update Format

```markdown
# Product Stakeholder Update: [Project/Team Name] - [Month/Quarter]

## 1. Executive Summary
*   **Overall Health:** [Green / Yellow / Red]
*   **Key Accomplishment:** [What major outcome did we drive since the last update?]

## 2. Outcome & Metric Performance
*   **North Star Metric:** [Current value vs. Target]
*   **Active Proxy Metric:** [e.g., % of teams with 3+ members active in Week 1 is at 42%, up from 35%]
*   **Experiment Learnings:** [What did we learn from recent A/B tests or discovery interviews?]

## 3. Current Work (Now Horizon)
*   [Feature A] - 6-week cycle ending [Date]. Status: [On Track (Downhill) / High Risk (Uphill)].
*   [Feature B] - 2-week cycle ending [Date]. Status: [Completed].

## 4. Next Priorities (Next Horizon)
*   [Shaping theme 1] - Target Opportunity: [Describe user pain point].
*   [Shaping theme 2] - Target Opportunity: [Describe user pain point].

## 5. Strategic Risks & Asks
*   [State any organizational blockers, dependencies, or budget requests clearly.]
```
