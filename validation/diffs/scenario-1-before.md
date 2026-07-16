# Validation Scenario 1: Team Workspaces PRD

This artifact represents the output of Workflow A under the `product-management` skill, applying the Context Gate and selecting the Shape Up Pitch model.

---

## 1. Context Gate (Mandatory)
*   **Strategy Context / ICP:** Note-taking app power users working in collaborative teams of 3–15 members who need to share project files. This aligns with our Q3 goal of "Expanding B2B collaborative engagement."
*   **Evidence Base:** Citing User Interview Report Doc L3 showing 8 out of 10 users share login credentials or copy-paste notes to share content with coworkers.
*   **Stage & Constraints:** Series A startup, single product engineering team, 6-week cycle appetite.

## 2. School Selection & Justification
*   **Selected School:** Shape Up Pitch (Ryan Singer)
*   **Justification:** We have a strict 6-week cycle appetite and a single engineering team. A Shape Up Pitch allows us to define rigid scope boundaries to prevent run-away feature creep, while leaving specific implementation details to the developers. Refer to the conflicts framework in `../product-management/references/conflicts.md#1-process-shape-up-vs-prdspec-culture`.

---

# Shaped Pitch: B2B Team Workspaces

## 1. Appetite
*   6 weeks (Big Batch cycle).

## 2. Solution Boundaries (Breadboard)
`[Notes List] -> (Click "Create Workspace") -> [Setup Workspace Modal] -> (Enter Name & Domains) -> [Workspace Dashboard] -> (Invite Teammates via Email Link)`

## 3. UI Boundaries (Fat Marker Sketch Description)
*   **Workspace Creator:** A simple button on the sidebar below the personal note folders.
*   **Setup Modal:** A text field to input the workspace name and a text area for allowed email domains (e.g., `company.com`).
*   **Dashboard Layout:** A two-pane sidebar. The left sidebar shows the list of collaborative folders. The main pane displays the active notes. No complex drag-and-drop file organization is included in this cycle.

## 4. Explicit Out of Bounds (No-Gos)
*   No custom role-based access control (RBAC) (all workspace members are admins).
*   No public URL link sharing for workspace folders (sharing is restricted to verified email domains).
*   No slack or third-party notification integrations (handled via simple in-app indicators).

## 5. Risks & Riskiest Assumptions
*   **Value Risk:** Users might continue copy-pasting notes instead of creating a workspace.
    *   *Test:* Add a mock "Create Workspace" sidebar link and measure CTR before final merge.
*   **Viability Risk:** Enterprise IT administrators blocking notes sharing due to security concerns.
    *   *Test:* PM reviews the sharing policy with our legal counsel and drafts a standard security whitepaper.
*   **Feasibility Risk:** Real-time collaborative editing conflicts.
    *   *Test:* Engineers perform a 2-day technical spike on our operational transformation (OT) engine to confirm it supports simultaneous edits in workspace folders.
