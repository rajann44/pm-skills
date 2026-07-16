# Validation Scenario 5: Backlog Prioritization & Roadmap

This artifact represents the output of Workflow D under the `product-management` skill, applying the Context Gate, Simple Prioritization, and Evidence Citations.

---

## 1. Context Gate (Mandatory)
*   **Strategy Context / ICP:** B2B Analytics Startup targeting Fintech mid-market BI teams. Active prioritization focus is **Monetization First**.
    *   *GEM Strategy Alignment Check:* The long-term product strategy (Scenario 3) ranks GEM as Engagement-first. However, due to a seed stage runway constraint (4 months remaining), we are pivoting to Monetization-first for this cycle to secure near-term ARR and survive. This mismatch is justified by our immediate viability constraints.
*   **Evidence Base:** Citing warehouse cost savings metrics reports and IT admin security request logs.
*   **Stage & Constraints:** Seed stage, 2 developers, 1 designer, fixed 6-week cycle appetite.

---

## 2. Simple Prioritization Matrix

We rate features based on their alignment with our Monetization priority, citing evidence or labeling them as assumptions. Refer to the execution reference in `../product-management/references/execution.md#5-prioritization-frameworks--rice-limits`.

| Feature | Strategic Impact | Effort / Cost | Evidence Citation |
| :--- | :--- | :--- | :--- |
| **SSO Support** | High | Medium | [Citing Security Request Log Doc L1 showing 3 enterprise deals blocked on SSO] |
| **Mobile Push Notifications** | Medium | Low | [Citing user onboarding funnel analytics showing 30% higher Day-7 retention when push is enabled] |
| **Slack Integration** | Low-Medium | Low | **[ASSUMPTION]** (No customer interviews have requested this yet) |
| **Dark Mode** | Low | Low | **[ASSUMPTION]** (Voted on public forum but no correlation to sales) |
| **CSV Export** | Medium | Low | [Citing active session logs showing 40% of users manual-copy data] |
| **Real-Time Collaboration** | High | High | [Citing User Interview Report Doc L3 showing sharing pain points] |
| **Audit Logs** | High | Medium | [Citing compliance checklist for Fintech SOC2 security review] |
| **Custom Dashboards** | Medium | High | **[ASSUMPTION]** (Unproven if custom dashboard BI improves retention) |

---

## 3. Capacity & Appetite Check
*   *Capacity constraint:* 2 developers, 1 designer, 6-week appetite.
*   *Selection:* We cannot build all "High Impact" features in one cycle. We fund **SSO Support** (High strategic value unblocking 3 deals) and **Mobile Push Notifications** (Medium strategic value, extremely low cost/effort, high onboarding impact) for the next cycle (fits the 6-week developer appetite). **Real-Time Collaboration** requires a technical spike and is moved to "Next" for discovery.

---

## 4. Now/Next/Later Roadmap

Structured around customer opportunities and outcomes without calendar dates. Refer to the templates in `../product-management/references/artifacts-templates.md#7-nownextlater-roadmap-template`.

| Time Horizon | Initiative / Customer Opportunity | Target Outcome OKR | Evidence Citation |
| :--- | :--- | :--- | :--- |
| **NOW** (Active Dev) | **SSO Support & Mobile Push Notifications**: Resolve enterprise security blocker and improve early user retention. | Unblock 3 target enterprise sales and increase Day-7 retention by 10%. | [Citing Security Request Log L1 and onboarding analytics] |
| **NEXT** (Discovery) | **Real-Time Collaboration**: Shape query-sharing and collaborative folders workflow. | Increase workspace sharing interactions by 20%. | [Citing User Interview Report L3] |
| **LATER** (Themes) | **AI Caching Insights**: Explore automated Snowflake optimization recommendations. | Reduce query costs by an additional 15%. | **[ASSUMPTION]** |
