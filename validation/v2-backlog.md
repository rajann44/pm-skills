# Deferred Feature Design: Automatic Stakes-Tiering (v2-backlog)

This document contains the product design for the **Automatic Stakes-Tiering** mechanism. It is genuinely deferred as a backlog item for the v2 release of the `product-management` agent skill.

---

## 1. Strategic Context & Rationale

In the v1 release, we implemented the manual `[DRAFT-ONLY]` / `[SANDBOX]` tags to solve Context Gate friction. This allows developers to explicitly tell the agent when to bypass the strict evidence-weight checks and substantive pushbacks.

However, relying on manual tags has a usability risk: users may forget to prepend tags, leading to frustrating pushbacks on simple tasks. In v2, if user telemetry triggers the conditions below, we will replace the manual tag with an **Automatic Stakes-Tiering Classifier** directly in `SKILL.md`.

---

## 2. Trigger Conditions (Usage Evidence)

We will pull the deferred auto-stakes-tiering design from the backlog and prioritize it for active development if usage logs show either of the following signals over a 30-day period:
1.  **Incorrect Interrogations (> 15%):** More than 15% of simple, low-risk requests (e.g., standard CSS fixes, copy changes, or tasks requiring < 30 lines of code) incorrectly trigger the Context Gate interrogation or License to Say No pushback because the user omitted the manual bypass tag.
2.  **User Friction Reports:** Direct user feedback indicates that entering a dialogue with the agent on simple backlog grooming is the primary source of tool adoption friction.

---

## 3. Auto-Stakes-Tiering Proposed Architecture

When triggered, the main `SKILL.md` router will automatically classify incoming prompts into one of two stakes-based tiers before executing the task:

```
                  ┌─────────────────────────┐
                  │    User Prompt Input    │
                  └────────────┬────────────┘
                               │
                [Auto-Stakes Classifier]
                               │
            ┌──────────────────┴──────────────────┐
            ▼                                     ▼
     [Low-Stakes Tier]                    [High-Stakes Tier]
   Appetite &lt; 2 Weeks                 Appetite &gt; 2 Weeks OR
    Styling, Copy, Docs                 Strategic Roadmap/PRD
            │                                     │
            ▼                                     ▼
  [Bypass Context Gate]                 [Enforce Context Gate]
  Direct Draft Output                    Evidence Check &amp; ICP
                                         License to Say No
```

### 3.1 Low-Stakes Tier (Auto-Bypass)
*   **Classification Criteria:**
    *   The prompt targets styling, layout, copy text, minor script refactoring, or localized unit test fixes.
    *   The implied development effort is clearly under **2 weeks** of appetite (e.g., single-file modifications).
*   **Behavior:** The Context Gate is automatically bypassed. The agent immediately outputs the draft or refactors the code without requesting strategic context or discovery evidence.

### 3.2 High-Stakes Tier (Strict Gate)
*   **Classification Criteria:**
    *   The prompt requests a new product feature, core database schema modification, payment gateway integration, strategic roadmap planning, or PRD drafting.
    *   The implied development effort is **> 2 weeks** (or is unspecified but describes a major initiative).
*   **Behavior:** The Context Gate is strictly enforced. The agent must verify the ICP, Strategy focus, and evidence weights, executing a **Substantive Pushback** if the evidence is insufficient.
