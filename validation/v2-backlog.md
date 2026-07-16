# Validation Scenario 10: Context Gate Bypass (v2-backlog)

This artifact represents the validation scenario for the `[DRAFT-ONLY]` and `[SANDBOX]` Context Gate bypass. It demonstrates how developers can bypass strict evidence weight requirements to quickly draft speculative backlog tickets.

---

## 1. User Request (With Bypass Tag)
> **User Prompt:** `[DRAFT-ONLY] Write a standard product spec for a direct integration with Slack. We want note sharing and channel updates.`

---

## 2. Agent Execution & Gate Evaluation

1.  **Bypass Tag Detection:** The agent scans the prompt and detects the `[DRAFT-ONLY]` tag.
2.  **Context Gate Bypass:** The agent suspends the requirement to establish a strategic ICP, evidence base (e.g. 5 interviews), or company stage constraints.
3.  **Substantive Pushback Bypass:** The agent skips the "License to Say No" pushback flow (speculative assumptions, falsifiable kill criteria, CEO decision framework).
4.  **Reference Routing:** The agent loads `./references/execution.md` and `./references/artifacts-templates.md` for standard spec conventions.
5.  **Output Generation:** The agent directly outputs the product spec, clearly labeled with the bypass banner.

---

## 3. Agent Output Spec

### [DRAFT-ONLY / SANDBOX BYPASS ACTIVE]

# Product Spec: Slack Direct Integration

*   **Status:** Draft / Sandbox Mode
*   **Description:** Allows users to share notes directly to Slack channels and receive automated channel updates when collaborative notes are updated.

---

## 1. Feature Specifications

### 1.1 "Send to Slack" Note Action
*   **UI:** Add a "Send to Slack" action in the note sharing menu.
*   **Behavior:**
    1.  User clicks "Send to Slack".
    2.  An OAuth popup requests permission to access the target Slack workspace (if not already authenticated).
    3.  User selects a channel from a searchable dropdown.
    4.  Note text is sent as a rich unfurled block in Slack.

### 1.2 Channel Activity Updates
*   **Behavior:**
    1.  If a collaborative note is edited by team members, a threaded reply is posted to the original Slack block summarizing the changes.
    2.  Frequency limit: Maximum 1 update post per channel per 5 minutes to prevent spamming.

---

## 2. Technical Scope Boundaries
*   No support for direct messaging (DMs); channel posts only.
*   No support for multi-workspace mapping; one note workspace links to one Slack workspace.
