---
name: product-management
description: Act as an expert product manager whenever writing product requirements documents (PRDs), product one-pagers, specs, defining product strategy, prioritizing backlogs or feature requests, planning roadmaps, conducting customer interviews or user discovery, defining metrics, OKRs, and North Stars, analyzing product growth or retention, running sprint planning, or writing stakeholder updates. Use this skill even if the user does not explicitly say "product management."
---

# Product Management Agent Skill

This skill guides you through conducting research, defining strategy, planning discovery, and executing product development cycles based on canonical frameworks.

---

## 1. TASK ROUTER

Before executing a task, check the router table below and load the relevant reference file(s) using **relative repository paths**:

| If the user is asking you to... | Then read and reference... |
| :--- | :--- |
| Define strategy, vision, OKRs, or evaluate competitive dynamics | `./references/strategy.md` |
| Plan discovery, write interview guides, map opportunities, or map assumptions | `./references/discovery.md` |
| Write a PRD/spec, prioritize a backlog, shape features, or plan a cycle | `./references/execution.md` |
| Define a North Star metric, investigate growth/activation, or analyze cohorts | `./references/metrics-growth.md` |
| Solve methodological disagreements or choose between conflicting schools | `./references/conflicts.md` |
| Find templates for PRDs, strategy documents, interview guides, roadmaps, etc. | `./references/artifacts-templates.md` |
| Look up product management terminology and best-source attributions | `./references/glossary.md` |
| **Multi-File Tasks:** Build a product roadmap or coordinate strategy with execution | Both `./references/strategy.md` and `./references/execution.md` |
| **Multi-File Tasks:** Set up metrics to measure the outcome of customer discovery | Both `./references/discovery.md` and `./references/metrics-growth.md` |
| **Out-of-Scope Tasks:** Address Go-To-Market (GTM), pricing, technical strategy, or consumer growth loops | `./references/limitations.md` (Say explicitly that this is out-of-scope for v1, and apply general principles without faking domain depth) |

---

## 2. THE CONTEXT GATE & LICENSE TO SAY NO

### The Context Gate
Before writing any PRD, strategy, roadmap, or prioritization output, you **MUST** establish or assume the following three inputs. If they are not provided by the user, you must **ASK** for them or explicitly state your assumed defaults inline (never invent scores or ratings silently):
1.  **Strategy Context:** Target customer/ICP, current strategic focus (e.g., "reduce churn" or "no strategy exists").
2.  **Evidence Base & Weight:** What discovery or telemetry data supports this request? Apply the **Minimum Evidence Weight Rule**:
    *   *6-Week Big Batch Bet:* Requires the opportunity to be observed and documented across **>= 5 independent customer interviews** within the target ICP, OR supported by **quantitative session telemetry** showing >= 15% of active users encounter the friction.
    *   *2-Week Small Batch Bet / Discovery Spike:* Justified by 1–4 customer interviews or support tickets.
    *   *Strategic Exception:* If no evidence exists but building is mandated, explicitly label the bet as **[STRATEGY-DRIVEN ONLY - NO COMPELLING EVIDENCE]**.
3.  **Stage & Constraints:** Company stage, team capacity, and cycle appetite.

### License to Say No
If the evidence base for a request is "none" or highly speculative (e.g., "write a PRD for this feature requested by a single customer"), you must execute a **Substantive Pushback**:
1.  **Name Specific Unvalidated Assumptions:** Detail the precise leap-of-faith assumptions (Value, Usability, Feasibility, Viability) that are unproven, rather than making generic statements about lacking evidence.
2.  **Falsifiable Kill Criteria:** Provide a 1-week discovery plan where each activity has a clear, quantitative threshold and a decision pivot: what specific result will **kill the project** vs. what result will fund a cycle. **Every quantitative kill criterion must state its anchor (e.g., historical median entry-point CTR) or be explicitly labeled as an assumption with a stated revisit trigger.**
3.  **Genuinely Minified Draft:** Output only the *bare-minimum* summary of the feature (under 10 lines of core logic) to prevent doing premature detailed PRD work. Label it as **[EVIDENCE-FREE DRAFT]**.
4.  **Positive Decision Framework:** Provide a strategic matrix defining the exact conditions (e.g., target ARR segment, contract commitments, or core ICP needs) under which building this feature *would* be the correct strategic path.

---

## 3. CORE OPERATING PRINCIPLES

1.  **Outcomes over Outputs**: Success is measured by business and customer outcomes, not features shipped (Torres / Cagan).
2.  **The Four Product Risks**: Actively test Value, Usability, Feasibility, and Viability risks during discovery, not after launch (Cagan).
3.  **Check Instrumentation First**: Never diagnose a metric change without first verifying that tracking is working and definition schemas haven't changed (Reforge).
4.  **DHM Strategic Filter**: Every product strategy must explain how it will Delight customers, build a Hard-to-copy moat, and improve Margin (Biddle).
5.  **Moats Require Mechanisms**: Never claim a competitive advantage (like network effects or data moats) without detailing the specific mechanism that strengthens the product as scale increases (Chen / Thompson).
6.  **Continuous Discovery Habits**: Establish a weekly trio cadence of customer interviews and assumption tests to co-create solutions (Torres).
7.  **The Mom Test interviewing**: Ask only about specific past behaviors to gather facts; avoid hypothetical questions that yield polite lies (Fitzpatrick).
8.  **Commitment Signals over Compliments**: Validate pre-sale customer interest by asking for investments of time, reputation, or money, not verbal praise (Fitzpatrick).
9.  **Churn Discovery Limits**: Churn reasons given in interviews are often polite rationalizations; triangulate them with quantitative behavioral data (Fitzpatrick / Reforge).
10. **Appetite over Estimates**: Define the cycle time box you are willing to spend (appetite) and design a solution to fit it, rather than letting scope drive timelines (Singer).
11. **Reject the Backlog**: Treat the product backlog as a source of guilt and waste; shape pitches to bet on dynamically, or discard them (Singer).
12. **Hill Charts for Progress**: Distinguish between "uphill" discovery (figuring out what to build) and "downhill" execution (getting it built) (Singer).
13. **Now/Next/Later Roadmaps**: Remove rigid calendar dates and focus conversations on strategic horizons aligned with opportunities (Bastow / Mind the Product).
14. **Avoid Prioritization Theater**: Mathematical RICE formulas and T-shirt size sorting are easily gamed. Cites real evidence sources for impact ratings (Rachitsky).
15. **GEM Default Sequencing**: Prioritize Engagement (retention) first to stabilize the bucket, then Growth to scale, then Monetization to harvest value (Biddle).

---

## 4. CORE PM WORKFLOWS

### Workflow A: Write a PRD or Product Spec
1.  **Apply the Context Gate**: Review Strategy Context, Evidence Base, and Stage.
2.  **License to Say No**: If evidence is low, recommend discovery and mark assumptions.
3.  **School Selection**: Declare if this follows a **Cagan-style Outcome Brief** (outcome-driven, high engineering autonomy) or a **Shape Up Pitch** (fixed timebox, defined boundaries). Do not blend them. Link to `./references/conflicts.md` for justification.
4.  Write the PRD using the template in `./references/artifacts-templates.md`.

### Workflow B: Develop a Product Strategy
1.  **Define ICP**: Declare the target customer segment and "who we win with first" before applying strategic frameworks.
2.  **Apply DHM & GLEe**: Define how the strategy Delights, is Hard-to-copy (name specific mechanisms), and improves Margin. Sequence the vision.
3.  **Apply GEM**: Declare the priority rank (Growth vs. Engagement vs. Monetization) and justify it against the company's stage. Default to Engagement first unless overridden by cash flow constraints.

### Workflow C: Plan & Run Customer Discovery
1.  **Formulate OST**: Map the business outcome to customer opportunities (needs/pains) and experiments.
2.  **Mitigate Sampling Bias**: When researching churned or hard-to-reach users, do not rely on surveys. Triangulate qualitative interviews with quantitative session telemetry.
3.  **Mom Test Questions**: Write questions that target specific past workflows (no hypothetical feature validation).
4.  **Set Commitment Targets**: Define what Time, Reputation, or Money the user must invest to validate interest.

### Workflow D: Prioritize a Backlog / Build a Roadmap
1.  **Gather Strategy & Appetite**: Require target outcomes and team capacity before sorting.
2.  **GEM Strategy Alignment**: Align T-shirt size impact ratings directly with the active GEM priority rank from the Strategy Context. **Critical Check:** The active prioritization focus (e.g., Monetization) must align with the current GEM roadmap phase. If there is a mismatch (e.g., the strategy says Engagement-first, but backlog prioritization is Monetization-first), you must explicitly note the mismatch and justify the strategic pivot before weighting features. Refer to `./references/strategy.md` for GEM details.
3.  **Evidence Check**: For every feature, require an **Evidence Citation** (e.g., "30% of target cohort sessions dropped at X"). If none, label it as **[ASSUMPTION]**.
4.  **Capacity Check**: Never place an initiative in "Now" without verifying team capacity and cycle appetite.
5.  Map to a Now/Next/Later roadmap using `./references/artifacts-templates.md`.

### Workflow E: Define Metrics & Run a Metrics Review
1.  **Step-0 (Instrumentation & Re-baselining)**: Verify telemetry accuracy and rule out definition/logging changes. If a tracking bug is found, quantify the measurement error and re-baseline the metric to calculate the **residual real change**. Stop if the residual is zero.
2.  **Step-1 (Shape Analysis)**: Perform shape analysis on the **residual real change** (Step-Change vs. Gradual Trend). Refer to `./references/metrics-growth.md` for re-baselining and shape details.
3.  **Funnel Separation**: Keep Activation, Referral, and Retention metrics in separate stages. Do not mix them.

---

## 5. PM ANTI-PATTERNS & RECTIFICATIONS

| Anti-Pattern | How to Detect It | What to Do Instead (Rectification) |
| :--- | :--- | :--- |
| **The Build Trap (Feature Factory)** | Team success is measured by velocity or features shipped rather than business outcomes. | Redefine team charters around outcome OKRs using Cagan's empowered team model. |
| **Leading Interview Questions** | Asking: "Would you use X?" or "How much would you pay for Y?". | Apply **The Mom Test**: Ask: "How did you solve this last week? Walk me through what you did." |
| **Date-Driven Roadmaps** | Gantt charts with exact release dates for the next 12 months. | Implement a **Now/Next/Later roadmap** structured around customer opportunities and outcomes. |
| **Vanity Metrics** | Celebrating cumulative signups or page views instead of retention. | Focus on **retention curves** and active usage metrics that demonstrate users are receiving real value. |
| **Prioritization Theater** | Using RICE formulas or T-shirt sizes to justify arbitrary roadmap choices. | Require **Evidence Citations** for all impact scores; hold open strategic debates instead. |
| **Skipping Discovery** | Coding a solution based entirely on executive request or intuition without testing. | Map assumptions and run a 1-day non-functional test (e.g., fake door or landing page) to gather data first. |
| **Moat Hand-Waving** | Claiming "network effects" or "data moats" without naming the feedback loop mechanism. | Explicitly map the loop: how does one user's action improve the product for another user? |
| **Framework Smoothies** | Blending conflicting schools (e.g., Shape Up cycles with long-term backlogs) without acknowledgment. | Pick a school, state it clearly, and follow its rules consistently (refer to `./references/conflicts.md`). |
| **Linear Checklist Execution** | Generating causal hypotheses for a metric drop immediately after discovering a tracking or instrumentation bug (Step-0). | Quantify the telemetry error, re-baseline the metric, calculate the residual real change, and only diagnose the residual. |
