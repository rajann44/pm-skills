# Validation Scenario 1: Team Workspaces PRD

This artifact represents the output of Workflow A under the `product-management` skill, applying the Context Gate (Minimum Evidence Weight Rule) and selecting the Shape Up Pitch model.

---

## 1. Context Gate (Mandatory)
*   **Strategy Context / ICP:** Note-taking app power users working in collaborative teams of 3–15 members who need to share project files. This aligns with our Q3 goal of "Expanding B2B collaborative engagement."
*   **Evidence Base & Weight:** Citing User Interview Report Doc L3. Upon auditing this source, it contains transcripts of only **3 independent customer interviews**.
*   **Pivot Decision (Evidence Weight Rule):** According to the Context Gate guidelines in `../product-management/SKILL.md#the-context-gate`, 3 interviews is < 5 and cannot justify a high-stakes 6-week cycle. We must reduce the cycle appetite to a **2-week Small Batch** (minimal functional test) or a discovery spike, scaling down the scope accordingly.
*   **Stage & Constraints:** Series A startup, 1 product team, strict 2-week cycle constraint.

## 2. School Selection & Justification
*   **Selected School:** Shape Up Pitch (Ryan Singer)
*   **Justification:** Given the constrained 2-week appetite, we choose a Shape Up Pitch to define rigid boundaries and prevent any runaway design or dev work. Refer to the conflicts framework in `../product-management/references/conflicts.md#1-process-shape-up-vs-prdspec-culture`.

---

# Shaped Pitch: B2B Team Workspaces (2-Week Small Batch)

## 1. Appetite
*   2 weeks (Small Batch).

## 2. Solution Boundaries (Breadboard)
`[Notes List] -> (Click "Share Folder") -> [Generate Invite Link] -> (Copy Link) -> [Invited User View (Read-Only list of notes)]`

## 3. UI Boundaries (Fat Marker Sketch Description)
*   **Share Folder Link:** A small link next to folder headers. Clicking generates a unique link.
*   **Invited User Screen:** A static notes index page containing shared documents. No workspace settings, custom domains, or workspace sidebar folders.

## 4. Explicit Out of Bounds (No-Gos)
*   No real-time editing (shared folders are read-only in this cycle to avoid OT database spikes).
*   No workspace creation or organization directories.
*   No custom member management UI (sharing is direct-link access only).

## 5. Risks & Riskiest Assumptions
*   **Value Risk (High):** Will read-only sharing satisfy users, or will they revert to credential sharing?
    *   *Test:* Measure the number of times shared folders are read-only viewed vs. shared folder links generated.
*   **Feasibility Risk (Low):** Building link generation and authentication takes less than 3 developer days.
*   **Viability Risk (Low):** Covered under existing database and routing configurations.
