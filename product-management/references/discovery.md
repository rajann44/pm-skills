# Product Discovery Reference

This document provides guidelines for customer discovery, opportunity mapping, and assumption validation, ensuring that product teams mitigate risks before writing production code.

---

## TABLE OF CONTENTS
- [1. Continuous Discovery Habits](#1-continuous-discovery-habits)
- [2. Opportunity Solution Trees (OST)](#2-opportunity-solution-trees-ost)
- [3. Assumption Mapping & Testing](#3-assumption-mapping-testing)
- [4. The Mom Test (Customer Interviewing)](#4-the-mom-test-customer-interviewing)
- [5. Churn Interview Limits & Telemetry Triangulation](#5-churn-interview-limits--telemetry-triangulation)
- [6. Commitment & Advancement Signals](#6-commitment--advancement-signals)

---

## 1. Continuous Discovery Habits

*   **Definition:** A weekly cadence of discovery activities (customer interviews, assumption testing) where a cross-functional product trio (PM, Designer, Tech Lead) co-creates solutions with customers.
*   **When to use:** Use this for established products to guide incremental iteration, product optimization, and backlog refinement.
*   **When NOT to use:** Do not use for highly speculative research on non-existent technology.
*   **Prerequisites:** Auto-recruited customer panel or pipeline to allow weekly scheduling.
*   **Worked Example:** A billing team schedules weekly interviews with finance admins using a automated system that offers a $50 gift card. In every interview, the trio hears the admin walk through how they processed their latest month-end invoices, identifying recurring bugs and usability issues that the team prioritizes in the next cycle.
*   **Source URL:** [producttalk.org/continuous-discovery-habits](https://www.producttalk.org)

---

## 2. Opportunity Solution Trees (OST)

*   **Definition:** A visual mapping tool that links a single business outcome (the goal) to verified user opportunities (needs, pains, desires), potential solutions, and rapid experiments.
*   **When to use:** Use this during discovery to organize brainstorms, structure user research, and justify roadmap priorities to stakeholders.
*   **When NOT to use:** Do not use when the outcome cannot be measured.
*   **Prerequisites:** A clear, quantitative target business outcome must be defined.
*   **Worked Example:**
    *   *Outcome:* Increase monthly active users (MAU) of a food app by 10%.
    *   *Opportunity:* "I struggle to decide what to eat for dinner."
    *   *Solution:* Add a randomized "Surprise Me" recipe selector button.
    *   *Experiment:* Add a mock button in the UI and measure click-through rate (CTR) to see if users are interested before building.
*   **Source URL:** [producttalk.org/opportunity-solution-tree](https://www.producttalk.org)

---

## 3. Assumption Mapping & Testing

*   **Definition:** The process of identifying and prioritizing the underlying leap-of-faith assumptions for a proposed solution across the four key risks: Value, Usability, Feasibility, and Business Viability.
*   **When to use:** Use this before writing code for any major new feature to avoid wasting engineering resources.
*   **When NOT to use:** Do not use for minor bug fixes or standard optimization tasks.
*   **Prerequisites:** A mapped solution concept that has passed the basic strategy filter.
*   **AI Value Risks (Conversational Friction):** When evaluating AI features (especially conversational chat interfaces in task-focused productivity workspaces like note-taking apps), the primary Value Risk is often **interaction friction**, not LLM performance. Conversational chat is a high-cognitive-load, slow-input interface compared to keyboard shortcuts, inline auto-complete, or direct visual menus.
    *   *Rule:* You must explicitly test if conversational prompting disrupts the user's active writing workflow.
    *   *Test:* Run a "wizard-of-oz" or click-through test comparing a chat text-prompt drawer against a single-click "summarize notes" shortcut. If users choose the prompt drawer less than 20% of the time, reject the conversational chat UI in favor of structured UI buttons.
*   **Worked Example:** Adding a B2B team-sharing workspace.
    *   *Critical Value Assumption:* Admins will allow employees to share company data externally.
    *   *Test:* Instead of building the backend for workspaces, the team drafts a legal policy document and email template, asking enterprise admins if they would sign off on it. Only when 70% of admins agree does the team proceed.
*   **Source URL:** [svpg.com/articles](https://svpg.com/articles/)

---

## 4. The Mom Test (Customer Interviewing)

*   **Definition:** A framework for talking to customers that extracts objective facts about past behavior rather than opinions, guesses, or polite compliments about future product ideas.
*   **When to use:** Use this during early customer discovery, problem validation, and generative research.
*   **When NOT to use:** Do not use for testing interactive prototypes.
*   **Prerequisites:** Direct, conversational access to customers who are in your target ICP.
*   **The Mom Test Rules:**
    1.  Talk about their life (past specific workflows) instead of your idea.
    2.  Ask about specifics in the past instead of generics or opinions about the future.
    3.  Talk less and listen more.
*   **Worked Example:**
    *   *Bad Question:* "Would you buy a mobile app that helps you manage your gym workouts?" (Produces polite lies).
    *   *Good Question:* "How did you plan your workouts last week? What tools did you use? Walk me through how you tracked your last workout." (Produces raw facts).
*   **Source URL:** [momtestbook.com](https://www.momtestbook.com)

---

## 5. Churn Interview Limits & Telemetry Triangulation

*   **The Problem:** The Mom Test interviewing style has a critical scope limit: **it is highly weak when investigating churned users**. Churned users often give polite rationalizations or false reasons for leaving (e.g., "I just didn't have time" or "It's too expensive") because they want to end the call quickly and avoid confrontation.
*   **Mitigation Strategy (Telemetry Triangulation):**
    1.  **Never rely solely on interviews or surveys for churn reasons.**
    2.  **Triangulate Qualitative Data with Session Telemetry:** Before interviewing a churned user, review their actual behavioral session logs. Look for:
        *   Did they drop off during a specific onboarding step?
        *   Did they encounter a crash or lag?
        *   Did they fail to reach the "Activation" milestone?
    3.  **Address Sampling Bias:** Churned users who agree to speak with you represent a biased sample (often highly vocal outliers). Mitigate this by offering compelling incentives ($100 gift cards), studying "proxy populations" (users who have dropped in activity but haven't formally canceled yet), and scaling behavioral analysis across the entire database to see where the majority of drop-offs occur.
*   **Worked Example:** A PM interviews a churned user who claims, "I left because we decided to cut budget." The PM reviews the user's session telemetry and discovers the user logged in twice, spent 12 minutes struggling on the integrations setup page, and encountered three database latency errors. The PM concludes the true cause was usability and feasibility, not price.

---

## 6. Commitment & Advancement Signals

*   **Definition:** A mechanism for validating customer interest during discovery meetings by requiring users to give up something of value (Time, Reputation, or Money) to advance.
*   **Scope Limits:** Commitment signals validate pre-sale problem intensity. They do not validate churn causes (as churned users want to disengage, not advance).
*   **When to use:** Use this at the end of discovery or customer interviews to evaluate if a user’s interest is genuine.
*   **When NOT to use:** Do not use when researching churn or during general customer support.
*   **Step-by-step Application:**
    1.  **Ask for Time:** "Would you be willing to run a 1-hour feedback trial with your team next Tuesday?"
    2.  **Ask for Reputation:** "Can you introduce me to your IT security director so we can clear the privacy review?"
    3.  **Ask for Money:** "We are taking $100 refundable deposits to secure early access. Would you like to put one down?"
    4.  **Evaluate:** If they refuse to invest any of these, treat their previous compliments as noise.
*   **Worked Example:** A B2B PM interviews a prospect who says, "This tool is exactly what we need." The PM responds, "Great. To get this set up, I need to coordinate with your IT security director. Can you introduce me to them via email today?" If the user hesitates, the interest is not validated.
*   **Source URL:** [momtestbook.com](https://www.momtestbook.com)
