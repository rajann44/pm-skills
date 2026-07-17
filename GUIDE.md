# Product Management Skill User Guide

This guide describes how to configure, run, and customize the `product-management` agent skill.

---

## Table of Contents
1. [Five-Minute Quickstart](#1-five-minute-quickstart)
2. [What This Skill Will (and Won't) Do](#2-what-this-skill-will-and-wont-do)
3. [Set Up Your Workspace (The 10x Unlock)](#3-set-up-your-workspace-the-10x-unlock)
4. [The Workflows — A Recipe Per Job](#4-the-workflows--a-recipe-per-job)
5. [Tags, Commands & Banners Reference](#5-tags-commands--banners-reference)
6. [Getting Better Answers (Power Usage)](#6-getting-better-answers-power-usage)
7. [Troubleshooting / FAQ](#7-troubleshooting--faq)

---

## 1. Five-Minute Quickstart

### Step 1: Install the Skill
Add the skill to your active workspace directory by running:
```bash
npx skills add https://github.com/rajann44/pm-skills --skill product-management
```

#### No Terminal? No Problem (Claude Desktop & Web UIs)
If you do not use Claude Code or Cursor in a terminal, you can easily load the skill into Claude Desktop Projects, custom GPTs, or Co-workers:
1.  **Upload Core Files:** Create a new Claude Project or custom GPT, and upload `product-management/SKILL.md` along with the contents of the `product-management/references/` folder as project knowledge documents.
2.  **Upload Workspace State:** Upload your local strategy files (`product/strategy.md` and `product/bets.md`—see Section 3 below) directly as active project documents. The agent will read them automatically to resolve the Context Gate.


### Step 2: Try Your First Prompt
Run the following prompt in your agent environment:
> **Prompt:** `Help me prioritize these 4 features for my SaaS app: 1. Dark Mode, 2. CSV Export, 3. Slack Integration, 4. Audit Logs.`

### Step 3: Respond to the Context Gate
Because this is a new workspace, the skill's **Context Gate** will intervene. The agent will halt and ask you for three diagnostic inputs:
1.  **Strategy Context:** What customer segment are you targeting (ICP) and what is the strategic focus?
2.  **Evidence Base:** Do you have telemetry or customer interviews justifying these features?
3.  **Constraints:** What is your cycle appetite (e.g. 2 weeks or 6 weeks) and team capacity?

To bypass the gate quickly and get your first result, reply:
> **Response:** `ICP is Series A store managers. Strategy focus is Engagement. No telemetry exists yet, let's treat these as small-batch experiments with a 2-week cycle appetite.`

### Step 4: Avoid Future Interrogation
To prevent the agent from asking these questions every time, run the setup command:
```
initialize workspace state
```
This interviews you once to generate local files that the skill reads automatically thereafter.

---

## 2. What This Skill Will (and Won't) Do

### What It Will Do
*   **Resolve Strategic Mismatches:** Compares new feature requests against your recorded strategic focus.
*   **Enforce Evidence Weights:** Restricts cycle lengths (e.g. refusing a 6-week build unless supported by >= 5 qualitative interviews or >= 15% telemetry signals).
*   **Substantively Push Back:** Rejects speculative, unbacked feature ideas with unvalidated assumptions and quantitative kill criteria.
*   **Log and Analyze Decisions:** Appends predictions to `product/decisions.md` and reviews them using the Retro workflow (`review my decision journal`).

### What It Won't Do
*   **Bypassed Spine Removal:** Using `[DRAFT-ONLY]` or `[SANDBOX]` tags allows the agent to skip interrogation and output a draft spec, but it **will not** remove inline `[ASSUMPTION]` labels and will still append a **Risk Note** for builds > 2 weeks.
*   **Go-To-Market & Pricing:** Does not write pricing strategies, launch plans, or sales scripts.
*   **Technical Architecture:** Does not design database schemas, API specs, or infrastructure layouts.
*   **Consumer Growth Loops:** Does not design virality loops, referral programs, or SEO pipelines.
*   **Silent Interrogation Bypass (No Filesystem):** If filesystem access is absent, the skill cannot read workspace strategy files and will fall back to asking diagnostic questions.

---

## 3. Set Up Your Workspace (The 10x Unlock)

To automate the Context Gate, initialize your workspace by running:
```
initialize workspace state
```
The agent will ask a few setup questions and generate two files under a new `product/` directory in your workspace root:

### `product/strategy.md` (Example Output)
```markdown
# Product Strategy Focus

*   **Last Updated:** 2026-07-18
*   **Target Customer (ICP):** Series A store managers needing automated inventory tracking.
*   **Active Strategic Focus:** Engagement
*   **Company Stage:** Early-stage SaaS (defaulting to Engagement first to validate PMF).
```

### `product/bets.md` (Example Output)
```markdown
# Active Bets & Timebox Appetites

*   **Standard Cycle Appetite:** 2-Week Small Batch Bets.
```

### How Workspace Loading Changes Behavior
Once these files exist, the skill loads them automatically. When you request a PRD or roadmap priority:
1.  **Header Citation:** The output is prepended with:
    `[RESOLVED FROM WORKSPACE: product/strategy.md (Last updated: 2026-07-18)]`
2.  **Staleness Alert:** If `product/strategy.md` has not been updated in **> 90 days**, the header displays:
    `[WARNING: Workspace strategy.md is >90 days old and may be stale. Run 'initialize workspace state' to update.]`
3.  **Contradiction Block:** If you ask for a feature that contradicts the focus in `product/strategy.md` (e.g. asking for a monetization upsell while focus is set to "Engagement"), the agent halts and surfaces:
    `[STRATEGIC CONTRADICTION DETECTED: Mismatch with focus 'Engagement' in product/strategy.md. Please provide a formal strategic justification or run 'initialize workspace state' to pivot strategy.]`

If filesystem capabilities are absent in the host environment, the skill automatically falls back to memory-based interrogation.

---

## 4. The Workflows — A Recipe Per Job

### Workflow D: Prioritize a Backlog / Build a Roadmap
*   **When to use:** Organizing, ranking, and scheduling feature backlogs without arbitrary numbers.
*   **Example Prompt:** `Prioritize the following backlog items: 1. CSV Transaction Export, 2. Dark Mode, 3. Slack Activity Webhooks.`
*   **Expected Output:**
    *   GEM alignment check showing feature relevance to strategic focus.
    *   Prioritization matrix with **Evidence Citations** or inline **[ASSUMPTION]** labels.
    *   Now/Next/Later roadmap mapped to capacity constraints.

### Workflow A: Write a PRD or Product Spec
*   **When to use:** Shaping a feature into a detailed engineering execution document.
*   **Example Prompt:** `Write a product spec for 'CSV Transaction Export'.`
*   **Expected Output:**
    *   Header citation and Strategic alignment.
    *   Mutually exclusive school selection: **[SECTION A: Outcome Brief Style (Marty Cagan)]** or **[SECTION B: Shaped Pitch Style (Shape Up)]**.
    *   Triage of the four product risks (Value, Usability, Feasibility, Viability).

### Workflow E: Define Metrics & Run a Metrics Review
*   **When to use:** Investigating a metric drop or defining key analytics funnels.
*   **Example Prompt:** `Verify and analyze this metrics drop: daily active users dropped 12% on iOS after yesterday's release.`
*   **Expected Output:**
    *   **Step-0 Instrumentation Check:** Isolating pipeline measurement errors to calculate the *residual real change*.
    *   **Step-1 Shape Analysis:** Classifying the drop shape (Step-Change vs. Gradual Trend).
    *   Separate funnel categorization (Activation vs. Retention vs. Referral).

### Workflow C: Plan & Run Customer Discovery
*   **When to use:** Drafting interview questions and testing opportunities.
*   **Example Prompt:** `Draft a customer interview guide to discover why merchants are abandoning the payout dashboard.`
*   **Expected Output:**
    *   `## 0. Quantitative Telemetry Context` block for behavioral session data.
    *   **Mom Test** questions focusing on past actions, avoiding hypothetical feature queries.
    *   Commitment target thresholds (investments of Time, Reputation, or Money).

### Workflow B: Develop a Product Strategy
*   **When to use:** Defining target segments, competitive moats, and business sequencing.
*   **Example Prompt:** `Help us outline our product strategy for a new merchant inventory management tool.`
*   **Expected Output:**
    *   ICP definition mapping "who we win with first".
    *   DHM evaluation (Delight, Hard-to-copy moat loops, and Margin rules).
    *   GLEe phase sequencing with quantitative phase exit metrics.

### Workflow F: Review Decision Journal (Retro)
*   **When to use:** Closing the prediction loop to calibrate decision accuracy and identify overconfidence bias.
*   **Example Prompt:** `review my decision journal`
*   **Expected Output:**
    *   **Under 10 Resolved Decisions (Small-Sample):** Outputs qualitative observations analyzing optimism bias (estimated vs. actual outcomes) and sunk cost boundary audits (failing bets kept active after meeting kill criteria). No statistical percentages or Brier scores.
    *   **10+ Resolved Decisions (Large-Sample):** Computes Brier Score, Sunk Cost Ratio, and Confidence Calibration Curve tables.
    *   *Resolving Entries:* To give the retro data, edit `product/decisions.md` and update `Status` to `Resolved` and append `Actual outcome: [Result]` to the entry.

---

## 5. Tags, Commands & Banners Reference

| Tag / Command / Banner | Type | Description & Behavior | When to Use |
| :--- | :--- | :--- | :--- |
| `initialize workspace state` | Command | Starts interactive interview to create `product/strategy.md` and `product/bets.md`. | Running the skill in a new workspace. |
| `review my decision journal` | Command | Reads `product/decisions.md` and conducts a calibration retro. | Reviewing launched feature accuracy. |
| `[DRAFT-ONLY]` or `[SANDBOX]` | User Tag | Lowers the Context Gate. Skips interrogation but preserves inline assumptions and risk notes. | Quick, speculative feature drafting. |
| `[DRAFT-ONLY / SANDBOX BYPASS ACTIVE]` | Banner | Prepended to outputs where the gate was bypassed. Bypassed runs are not journaled. | Identifying un-validated specs. |
| `[RESOLVED FROM WORKSPACE: ...]` | Banner | Header indicating strategy files were loaded successfully. | Standard gated outputs. |
| `[STRATEGIC CONTRADICTION DETECTED]` | Banner | Warning printed when a request contradicts the active strategic focus. | Catching strategy drift. |
| `[ASSUMPTION]` | Label | Inline tag flagging unproven ICPs, needs, or telemetry claims. | Pinpointing leaps of faith. |
| `[EVIDENCE-FREE DRAFT]` | Banner | Label applied to minified pushback drafts (<10 lines of core logic). | Reviewing raw ideas. |

---

## 6. Getting Better Answers (Power Usage)

1.  **Cites Telemetry Proactively:** Provide evidence counts proactively (e.g., '12 of 20 interviews mentioned X') and the gate accepts them without asking — evidence at or above the bar qualifies the request for larger cycle appetites.
2.  **Declare Your School:** Force-skip conflicts detours by explicitly naming your preference: `Use Marty Cagan outcome briefs` or `Use Shape Up cycle templates`.
3.  **Resolve Your Journal:** Keep `product/decisions.md` honest. Update actual outcomes even (especially) when predictions fail. The calibration Retro is only as accurate as its record.
4.  **Debate the Kill Criteria:** When the agent pushes back with falsifiable kill criteria, argue the metrics or thresholds in your response to refine the discovery plan, rather than re-prompting.

---

## 7. Troubleshooting / FAQ

*   **It keeps asking me questions.**
    *   *Fix:* Initialize your workspace files using `initialize workspace state`, or prepend your prompt with `[DRAFT-ONLY]` to skip interrogation.
*   **It refused to write my PRD.**
    *   *Reason:* The evidence weight was insufficient. Either add telemetry/interview metrics to the prompt, scale down your request to a 2-week discovery spike, or use `[DRAFT-ONLY]`.
*   **It flagged a strategic contradiction.**
    *   *Fix:* You must either provide a strategic justification in your prompt (e.g. how it converts to monetized seats), update your strategy focus in `product/strategy.md`, or bypass using `[DRAFT-ONLY]`.
*   **The Retro says it won't compute statistics.**
    *   *Reason:* Under the **Small-Sample Rule**, Brier scores and calibration percentages are disabled if you have fewer than 10 resolved entries in `product/decisions.md` to prevent false precision.
*   **It says my request is out of scope.**
    *   *Reason:* The skill is constrained to product strategy, discovery, metrics, and cycles. GTM launch marketing, pricing models, and technical coding architecture are handled by separate domains (see [limitations.md](./product-management/references/limitations.md)).
*   **The skill isn't triggering.**
    *   *Fix:* Make sure your prompt refers to product requirements, PRDs, prioritization, metrics, roadmaps, dashboard drops, or customer discovery.
