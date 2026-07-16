# Methodological Conflicts Reference

This document maps the major debates and conflicting schools of thought in modern product management, providing clear decision criteria for when to apply each approach.

---

## TABLE OF CONTENTS
- [1. Process: Shape Up vs. PRD/Spec Culture](#1-process-shape-up-vs-prdspec-culture)
- [2. Team Charter: Empowered Teams vs. Feature Teams](#2-team-charter-empowered-teams-vs-feature-teams)
- [3. Discovery Scale: Continuous Discovery vs. Classic MVP](#3-discovery-scale-continuous-discovery-vs-classic-mvp)
- [4. Prioritization: RICE/ICE Advocates vs. Critics](#4-prioritization-riceice-advocates-vs-critics)
- [5. Sequencing: Biddle's GEM vs. Monetization First](#5-sequencing-biddles-gem-vs-monetization-first)

---

## 1. Process: Shape Up vs. PRD/Spec Culture

*   **The Conflict:** Ryan Singer (*Shape Up*) rejects traditional product backlogs and detailed spec-style PRDs. He advocates for "shaping" work at a medium level of abstraction with breadboards/fat marker sketches and using 6-week betting cycles with circuit breakers. Conversely, traditional PRD/spec culture relies on PMs writing exhaustive requirements covering all edge cases before engineering estimation.
*   **The Positions:**
    *   *Shape Up (Ryan Singer):* Fix time (appetite), flex scope, shape abstractly, eliminate backlogs, bet on pitches.
    *   *PRD/Spec Culture:* Fix scope, estimate time, write detailed specs, groom a continuous backlog.
*   **Decision Criteria:**
    *   **Choose Shape Up if:** The team is cross-functional, highly collaborative, and has a high trust level; engineers want implementation autonomy; the team is drowning in backlog management; timelines are frequently slipping.
    *   **Choose PRD/Spec if:** Working in highly regulated or safety-critical fields (e.g., medical devices, core billing engines) where exact specs are contractually or legally required; or when working with outsourced/junior developers who need strict, step-by-step guidance.

---

## 2. Team Charter: Empowered Teams vs. Feature Teams

*   **The Conflict:** Marty Cagan (SVPG) argues that "feature teams" (which exist to build whatever features stakeholders or executives request) are a waste of engineering talent. He advocates for "empowered product teams" which are given a business problem to solve (outcome) and the autonomy to figure out how to solve it. However, many traditional organizations rely on feature teams because they want predictability, control over the roadmap, and direct fulfillment of sales promises.
*   **The Positions:**
    *   *Empowered Teams (Marty Cagan):* Cross-functional, aligned by outcome (OKRs), given problems to solve, accountable for business results.
    *   *Feature Teams:* Delivery-focused, aligned by output, given features to ship, accountable for delivery dates.
*   **Decision Criteria:**
    *   **Choose Empowered Teams if:** Product-market fit is established or being searched for in a highly dynamic market where the solution is unknown; the team possesses high design and engineering talent.
    *   **Choose Feature Teams if:** The business model is purely operational and execution-focused, where the exact feature requirements are dictated by customer contracts, regulatory updates, or executive strategy (e.g., enterprise B2B customized builds).

---

## 3. Discovery Scale: Continuous Discovery vs. Classic MVP

*   **The Conflict:** Teresa Torres (*Continuous Discovery Habits*) argues that building and launching a classic MVP is too slow and expensive. She advocates for continuous micro-discovery: breaking solutions down into smaller assumptions and testing them in 1-day or 1-week experiments (fake-door tests, landing pages, paper prototypes) before coding. Classic Lean Startup practitioners argue that micro-tests fail to validate the end-to-end user loop and payment conversion, which only a functional MVP can do.
*   **The Positions:**
    *   *Continuous Discovery (Teresa Torres):* Continuous weekly interviewing, assumption testing of micro-parts, co-creating with users.
    *   *Classic MVP (Eric Ries):* Build a minimum functional product, launch it to the public, measure end-to-end cohort behavior.
*   **Decision Criteria:**
    *   **Choose Continuous Discovery if:** Adding features to an existing product with a stable user base where the marginal cost of code is high, and you can run non-functional tests within the existing application shell.
    *   **Choose Classic MVP if:** Launching an entirely new business line or standalone startup where you must validate if a user will go through the entire end-to-end flow, pay money, and establish a recurring usage habit.

---

## 4. Prioritization: RICE/ICE Advocates vs. Critics

*   **The Conflict:** Prioritization frameworks like RICE are widely used to justify roadmap decisions with data. However, critics like Lenny Rachitsky warn that RICE often becomes "prioritization theater." PMs simply adjust the "Confidence" or "Impact" multipliers until their favorite feature gets the highest score. Critics advocate for subjective "Simple Prioritization" based on strategic alignment and T-shirt size impact-to-cost mapping, while enforcing Evidence Citations to prevent T-shirt size theater.
*   **The Positions:**
    *   *RICE/ICE Advocates:* Use mathematical formulas to objectify decisions, manage stakeholders, and weigh reach against effort.
    *   *RICE Critics:* Formulas are easily gamed. Use T-shirt sizes (XS-XL) and open strategic debates instead.
*   **Decision Criteria:**
    *   **Choose RICE if:** Operating in a highly political, large corporate environment with multiple competing stakeholders where you must defend roadmap choices with numbers.
    *   **Choose Simple Priority if:** Working in small, agile, high-trust startups or teams where alignment is achieved via open debate rather than spreadsheets.

---

## 5. Sequencing: Biddle's GEM vs. Monetization First

*   **The Conflict:** Gibson Biddle’s default GEM sequencing states that companies must first focus on **Engagement** (retention) to prove the product is good and has PMF; then **Growth** (acquisition) to scale the audience; and only then **Monetization** to extract value. However, many early-stage B2B founders and bootstrappers argue that this sequencing is a luxury of venture-backed consumer startups. They argue that **Monetization** must come first to prove willingness to pay and survive.
*   **The Positions:**
    *   *Engagement First (Biddle):* Retention is the ultimate metric. Do not grow a leaky bucket; do not monetize until you have proven retention.
    *   *Monetization First:* Willingness to pay is the ultimate validator. Monetize early to fund development and screen out low-intent users.
*   **Decision Criteria:**
    *   **Choose Engagement First (Biddle) if:** You are venture-backed with substantial runway, or operating a consumer/network-effects product where scale is the primary driver of value.
    *   **Choose Monetization First if:** You are bootstrapped, need immediate cash flow to survive, or operating in premium B2B enterprise SaaS where willingness to pay is the primary indicator of product value.
