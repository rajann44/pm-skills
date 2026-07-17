# Product Management Skill Cheat Sheet

A high-density reference sheet for daily product management cycles.

---

## 🚀 Prompts & Workflows

### 1. Prioritize a Backlog (Workflow D)
```markdown
Prioritize the following backlog items:
1. [Feature 1]
2. [Feature 2]
3. [Feature 3]
```

### 2. Draft a PRD / Spec (Workflow A)
```markdown
Write a product spec for '[Feature Name]'. Use [Marty Cagan outcome briefs | Shape Up cycle templates].
```

### 3. Diagnose a Metrics Drop (Workflow E)
```markdown
Verify and analyze this metrics drop: [Metric Name] dropped [X]% on [Platform/iOS] after [Event/Date].
```

### 4. Write an Interview Guide (Workflow C)
```markdown
Draft a customer interview guide to discover why [ICP segment] are abandoning [Feature/Flow].
```

### 5. Develop Product Strategy (Workflow B)
```markdown
Help us outline our product strategy for a new [Product Name].
```

### 6. Review Decision Journal (Workflow F)
```markdown
review my decision journal
```

---

## 🛠️ Setup & Maintenance Commands

*   **`initialize workspace state`**
    Initializes (or updates) `product/strategy.md` and `product/bets.md` via interview.
*   **`review my decision journal`**
    Conducts a retrospective calibration audit from `product/decisions.md`.

---

## 🏷️ Bypass & Control Tags

*   **`[DRAFT-ONLY]`** (or **`[SANDBOX]`**)
    Lowers the Context Gate. Skips interrogation but enforces inline `[ASSUMPTION]` tags and Risk Notes for >2 week builds. Bypassed specs are not written to the decision journal.

---

## 🛡️ Output Citation & Warning Banners

*   `[RESOLVED FROM WORKSPACE: product/strategy.md (Last updated: YYYY-MM-DD)]`
    Appears when Context Gate loads strategy context automatically from workspace files.
*   `[WARNING: Workspace strategy.md is >90 days old and may be stale. Run 'initialize workspace state' to update.]`
    Appears when the strategy context file is >90 days older than the current environment date.
*   `[STRATEGIC CONTRADICTION DETECTED: Mismatch with focus '<Focus>' in product/strategy.md. Please provide a formal strategic justification or run 'initialize workspace state' to pivot strategy.]`
    Fires when a request contradicts the active strategic focus (e.g. Monetization focus vs. Growth request).
*   `[ASSUMPTION]`
    Surfaced inline next to unverified claims, customer needs, or ICP definitions.
*   `[EVIDENCE-FREE DRAFT]`
    Applied to minified drafts (< 10 lines of core logic) generated during a pushback.
*   `[STRATEGY-DRIVEN ONLY - NO COMPELLING EVIDENCE]`
    Applied to cycles where building is strategically mandated but lacks telemetry or interview evidence.
