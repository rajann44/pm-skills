# Product Strategy Frameworks Reference

This document provides detailed guidelines for designing, aligning, and communicating product strategy using canonical industry frameworks.

---

## TABLE OF CONTENTS
- [1. Strategy Context: ICP First](#1-strategy-context-icp-first)
- [2. The DHM Model & Moat Mechanisms](#2-the-dhm-model--moat-mechanisms)
- [3. The GLEe Model](#3-the-glee-model)
- [4. The GEM Model & Sequencing Logic](#4-the-gem-model--sequencing-logic)
- [5. Aggregation Theory](#5-aggregation-theory)
- [6. Platform vs. Product Strategy](#6-platform-vs-product-strategy)
- [7. OKRs in Product Strategy](#7-okrs-in-product-strategy)

---

## 1. Strategy Context: ICP First

Before applying any strategic frameworks, you must define the **Ideal Customer Profile (ICP)**. A strategy that attempts to delight "everyone" is not a strategy.
*   **Definition:** The specific user segment that experiences the highest problem intensity and receives the maximum value from your product.
*   **Application Rule:** Begin every strategy document by stating: "Who do we win with first?" Define their specific workflows, constraints, and alternatives.

---

## 2. The DHM Model & Moat Mechanisms

*   **Definition:** A framework stating that a product strategy must define how the product will **Delight** customers, build a **Hard-to-copy** competitive advantage, and improve business **Margin** simultaneously.
*   **When to use:** Use this when defining or auditing a product's strategy to ensure it builds sustainable, long-term business value.
*   **When NOT to use:** Do not use for short-term cycle execution or troubleshooting daily operational bugs.
*   **Prerequisites:** Target ICP and customer problem segment must be explicitly defined.
*   **Moat Mechanisms (Hard-to-copy):** You cannot simply label a feature a "moat." You must define the *mechanism* by which the moat strengthens as the business scales:
    1.  **Network Effects:** Each new node (user) directly increases the utility of the product for existing nodes.
    2.  **Proprietary Data / Data Network Loop:** More user interaction data feeds into an algorithm, which improves the experience for all users, generating more data.
    3.  **High Switching Costs:** Deep workflow integration (e.g., custom APIs, databases) makes moving to a competitor cost-prohibitive in time and capital.
    4.  **Scale Economies:** Large-scale operations reduce marginal costs, allowing lower prices that competitors cannot match.
*   **Rule (ICP Stress-Test):** Every moat mechanism must be stress-tested against the chosen ICP's regulatory, data privacy, and commercial constraints. For example, a cross-company "data sharing loop" is legally and commercially impossible in highly regulated segments like B2B Fintech or healthcare due to compliance (SOC2, HIPAA, PCI-DSS) and confidentiality rules. A moat mechanism that cannot survive its own ICP's constraints is "moat theater" and must be replaced.
*   **Worked Example:** Netflix recommendation engine.
    *   *Delight:* Instant discovery, reducing search time to under 1 minute.
    *   *Hard-to-copy (Data Network Loop):* User viewing data feeds the recommendation algorithm. More viewing data → better recommendations → more watch time → more data. A new competitor with zero user history cannot replicate this accuracy.
    *   *Margin:* Personalized search decreases subscriber churn, directly boosting recurring monthly revenue.
*   **Source URL:** [gibsonbiddle.com/the-dhm-model](https://www.gibsonbiddle.com)

---

## 3. The GLEe Model

*   **Definition:** A phased sequencing framework to plan a product's multi-year evolution: **G**et Big on a beachhead, **L**ead in that space, and **E**xpand into adjacencies.
*   **When to use:** Use this when explaining a 10–15 year vision to boards, investors, and team members to sequence major initiatives.
*   **When NOT to use:** Do not use for mapping near-term feature roadmaps.
*   **Prerequisites:** High-level strategic alignment and financial runway to think beyond the current fiscal year.
*   **Worked Example:** Netflix
*   **GLEe Horizons & Exit Criteria:** For each horizon, you **must** define a quantitative **Phase Exit Metric** that serves as the transition trigger to the next horizon:
    1.  *Get Big:* Focus on a single, narrow customer opportunity or target segment. *Exit Metric:* Quantitative validation of initial product-market fit (e.g., "Achieve 40% weekly retention across 50 active B2B customer teams").
    2.  *Lead:* Leverage the initial win to lead the primary market. *Exit Metric:* Dominant market position metric (e.g., "Grow market share to 25% in target mid-market sector").
    3.  *Expand:* Expand into adjacent segments, products, or platforms. *Exit Metric:* Platform expansion metric (e.g., "Integrate 3 adjacent ecosystem platforms and drive 15% of ARR from expansion products").
*   **Source URL:** [gibsonbiddle.com/glee-model](https://www.gibsonbiddle.com)

---

## 4. The GEM Model & Sequencing Logic

*   **Definition:** An alignment framework (Biddle) that forces an organization to prioritize and rank **Growth**, **Engagement** (retention), and **Monetization** based on their specific business context. Biddle emphasizes that the relative ranking of these three metrics is a context-dependent exercise that evolves as a company matures.
*   **Sequencing Logic:** While Biddle does not dictate a universal sequence, this skill implements a default strategic recommendation of **Engagement first, then Monetization, then Growth** for early-stage software products to ensure unit economics and retention loops are validated before scaling:
    1.  *Engagement (Retention) First:* Prove the product is good and has product-market fit (PMF). Growing a product with poor engagement is like pouring water into a leaky bucket.
    2.  *Monetization Second:* Verify unit economics and willingness to pay before committing capital to customer acquisition.
    3.  *Growth Third:* Scale the user base once retention and monetization loops are validated.
*   **Justifying Variations:** The product team must explicitly define and justify their current rank order. For example, a VC-funded consumer application might prioritize Growth before Monetization, whereas a bootstrapped SaaS company or a seed-stage startup with low runway must rank Monetization first to survive.
*   **When to use:** Use this during quarterly or annual planning to align product, marketing, finance, and engineering leaders on the primary focus of the business.
*   **When NOT to use:** Do not use to prioritize individual product features.
*   **Worked Example:** Netflix in 2005 prioritized Monetization first to prove profitability to Wall Street during Blockbuster's price war.
*   **Source URL:** [gibsonbiddle.com/gem-model](https://www.gibsonbiddle.com)

---

## 5. Aggregation Theory

*   **Definition:** An economic framework explaining how value in digital markets is captured by companies that aggregate user demand through a superior user experience, rather than companies that control supply or physical distribution.
*   **When to use:** Use this to analyze market structures, design business models, and evaluate the competitive threat of digital giants.
*   **When NOT to use:** Do not use for user research or small usability feature design.
*   **Prerequisites:** The market must operate digitally with near-zero marginal distribution and transaction costs.
*   **Worked Example:** Google Search aggregates demand by providing the best search index. Because all consumers search on Google, publishers must optimize their content for Google, reinforcing Google's dominance.
*   **Source URL:** [stratechery.com/concepts](https://stratechery.com/concepts/)

---

## 6. Platform vs. Product Strategy

*   **Definition:** A framework contrasting a "Product" (a closed, end-to-end solution delivered directly to users) with a "Platform" (an infrastructure or developer ecosystem that enables third parties to build their own products and businesses).
*   **When to use:** Use this when designing API strategies or deciding how to compete against dominant industry aggregators.
*   **When NOT to use:** Do not use during early MVP development when the product has not yet established a core value proposition.
*   **Worked Example:** Shopify is a Platform. Shopify provides the checkout, inventory, and storefront APIs, allowing merchants to build independent brands. Shopify succeeds only when its merchants succeed. Refer to `./conflicts.md` to see the strategic trade-offs between Platform and Product paths.
*   **Source URL:** [stratechery.com/concepts](https://stratechery.com/concepts/)

---

## 7. OKRs in Product Strategy

*   **Definition:** A strategic alignment process that maps high-level product strategy to empowered teams through Objectives (qualitative goals) and Key Results (quantitative, outcome-oriented metrics).
*   **When to use:** Use this to coordinate product organizations, ensuring teams have clear direction without micro-management.
*   **When NOT to use:** Do not use as a performance evaluation tool or as a checklist of tasks (output OKRs).
*   **Worked Example:** Spotify search team OKR.
    *   *Objective:* Make it effortless for users to find the music they want.
    *   *Key Result 1:* Reduce average search-to-play time from 12 seconds to 8 seconds.
    *   *Key Result 2:* Increase the click-through rate of search autocomplete suggestions by 15%.
*   **Source URL:** [svpg.com/articles](https://svpg.com/articles/)
