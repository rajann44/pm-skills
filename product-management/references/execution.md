# Product Execution & Delivery Reference

This document provides detailed guidelines for shaping work, managing delivery cycles, roadmapping, prioritizing backlogs, and running product reviews.

---

## TABLE OF CONTENTS
- [1. Shape Up: Appetite vs. Estimates](#1-shape-up-appetite-vs-estimates)
- [2. Shape Up: Shaping, Betting & Rejection of Backlogs](#2-shape-up-shaping-betting--rejection-of-backlogs)
- [3. Shape Up: Circuit Breakers & Hill Charts](#3-shape-up-circuit-breakers--hill-charts)
- [4. Now/Next/Later Roadmaps](#4-nownextlater-roadmaps)
- [5. Prioritization: RICE Limits & T-Shirt Size Theater](#5-prioritization-rice-limits--t-shirt-size-theater)
- [6. Running Product Reviews](#6-running-product-reviews)

---

## 1. Shape Up: Appetite vs. Estimates

*   **Definition:** A resource management policy where a team starts by defining a fixed timebox (an "Appetite," e.g., 2 weeks or 6 weeks) they are willing to spend to solve a problem, and then designs a solution to fit that window, rather than letting the scope dictate the timeline.
*   **When to use:** Use this in fast-moving, highly ambiguous environments to prevent timeline slippage and scope creep.
*   **When NOT to use:** Do not use for contract-driven client services that guarantee a fixed scope on a fixed date.
*   **Prerequisites:** Clear understanding of the problem boundaries.
*   **Worked Example:** Building a calendar view.
    *   *Traditional Agile:* Estimate tasks (calculated at 12 weeks), then run sprints.
    *   *Shape Up:* Declare a 6-week appetite. Design a read-only monthly view. Omit drag-and-drop event moving and weekly/daily views, ensuring the feature ships in 6 weeks.
*   **Source URL:** [basecamp.com/shapeup](https://basecamp.com/shapeup)

---

## 2. Shape Up: Shaping, Betting & Rejection of Backlogs

*   **Definition:** **Shaping** is pre-development work that defines a project's boundaries at a medium level of abstraction (using breadboards and fat marker sketches) so it is concrete enough to build but flexible enough for developers to design the details. **Betting** is a quarterly/cycle meeting where leadership reviews shaped pitches and commits to them.
*   **Backlog Rejection:** Shape Up explicitly rejects the concept of a product backlog. Ryan Singer argues that maintaining a backlog is a wasteful process that creates guilt. Instead, ideas are either pitched at the Betting Table or discarded. If an idea is truly important, it will resurface naturally when the timing is right.
*   **When to use:** Use this to bridge the gap between high-level product design and software engineering, and to eliminate backlog grooming overhead.
*   **When NOT to use:** Do not use in command-and-control organizations where senior executives demand a detailed 12-month feature roadmap.
*   **Step-by-step Application:**
    1.  **Breadboarding:** Map the user's flow using text labels and connection arrows (no UI elements).
    2.  **Fat Marker Sketches:** Draw rough UI layouts using thick markers, making details impossible to represent.
    3.  **Draft a Pitch:** Document the problem, appetite, solution boundaries, out-of-bounds, and risks.
    4.  **The Betting Table:** Review shaped pitches during the "cool-down" week and decide which ones to fund for the next cycle.
*   **Worked Example:** Shaping a "custom invoice template" feature. The breadboard shows `Invoice Editor -> Click Template -> Select Theme -> Preview -> Save`. The pitch explicitly states: "No custom HTML uploads."
*   **Source URL:** [basecamp.com/shapeup](https://basecamp.com/shapeup)

---

## 3. Shape Up: Circuit Breakers & Hill Charts

*   **Definition:** **Circuit Breakers** are a policy stating that if a project is not completed within its cycle, the project is canceled and the team is reassigned. No automatic extensions are granted. **Hill Charts** track project progress by dividing work into two phases: the "uphill" phase (figuring out what to do) and the "downhill" phase (execution).
*   **When to use:** Use this to prevent projects from dragging on indefinitely (sunk cost fallacy) and to gain visibility into real progress without status report overhead.
*   **When NOT to use:** Do not use for routine bug triage or maintenance operations.
*   **Worked Example:** A team is building a reporting dashboard. By week 4 of a 6-week cycle, the database query performance is still stuck "uphill" (unsolved). The Hill Chart signals high risk. In week 6, the dashboard remains unfinished. The Circuit Breaker fires: the project is paused, and the team moves to the cool-down phase while leadership decides whether to re-bet.
*   **Source URL:** [basecamp.com/shapeup](https://basecamp.com/shapeup)

---

## 4. Now/Next/Later Roadmaps

*   **Definition:** A roadmap format that replaces rigid timeline dates with three prioritized time horizons: **Now** (active development; high certainty), **Next** (in discovery/shaping; medium certainty), and **Later** (strategic directions; low certainty).
*   **When to use:** Use this to manage stakeholder expectations, maintain product agility, and focus discussions on value and strategy rather than calendar dates.
*   **When NOT to use:** Do not use in contract-driven enterprise B2B sales cycles where clients require contractually guaranteed delivery dates.
*   **Worked Example:** A SaaS startup uses a Now/Next/Later roadmap.
    *   *Now:* Stripe billing migration (Target: Reduce billing failure rate by 15%).
    *   *Next:* Interactive dashboard builder (Target: Increase dashboard creation rates).
    *   *Later:* Multi-currency localization support (Target: Enable EU expansion).
*   **Source URL:** [mindtheproduct.com](https://www.mindtheproduct.com)

---

## 5. Prioritization: RICE Limits & T-Shirt Size Theater

*   **The Problem:** Traditional mathematical prioritization (like RICE: Reach, Impact, Confidence, Effort) is highly prone to **RICE theater**—where PMs manipulate confidence and impact scores to justify their pre-selected features.
*   **T-Shirt Size Theater (The Same Disease):** Swapping RICE for T-shirt sizing (XS, S, M, L, XL) often leads to the same disease in a different costume. PMs subjectively label their favorite features as "High Impact / Low Cost" without any evidence, leading to biased roadmap decisions.
*   **The Rectification (Evidence Citations):**
    1.  **Forbid subjective scoring.** Every Impact and Effort rating must cite a specific evidence source (e.g., "Impact: L [Citing Discovery Interview Report Doc X showing 80% of segment experience this]"; "Effort: M [Citing engineering spike review Y]").
    2.  If no evidence exists, the rating must be explicitly labeled as **[ASSUMPTION]**.
    3.  Refer to `./conflicts.md` to see the debate on mathematical vs. simple prioritization.
*   **Worked Example:**
    *   *T-Shirt Theater:* PM rates "SSO support" as High Impact, Low Cost to get it prioritized.
    *   *Rectified Prioritization:* PM rates "SSO support": Impact: L [Citing Strategy Doc L2 showing 3 enterprise prospects blocked on SSO]; Effort: H [Citing Tech Lead spike note showing Cognito migration required].
*   **Source URL:** [lennysnewsletter.com](https://www.lennysnewsletter.com)

---

## 6. Running Product Reviews

*   **Definition:** A structured governance meeting where cross-functional leadership reviews product strategy, metrics, and progress to ensure alignment, share experiment results, and make investment decisions.
*   **When to use:** Use this on a recurring monthly or quarterly basis to maintain organizational trust and visibility.
*   **When NOT to use:** Do not use as a status-update meeting or a design-critique session.
*   **Worked Example:** A quarterly product review meeting at an enterprise software firm. Instead of team-by-team status updates, the VP of Product presents the GEM model alignment, shares why a 6-week cycle was canceled via the circuit breaker, and opens a debate on shifting resources to a new enterprise security theme.
*   **Source URL:** [review.firstround.com](https://review.firstround.com)
