# Validation Scenario 6: Chatbot PRD Pushback (Adversarial)

This artifact represents the output of Workflow A under the `product-management` skill, applying the **License to Say No** to an evidence-free executive request.

---

## 1. Context Gate Evaluation
*   **Strategy Context / ICP:** Power users of note-taking app. No strategic goal exists for AI integrations in our current Q3 plan.
*   **Evidence Base:** **None**. Zero telemetry events or user support tickets indicate users are struggling with note discovery via standard search, or that they desire a chat interface.
*   **Stage & Constraints:** Early-stage startup, limited team capacity, strict 6-week cycle constraints.

---

## 2. Substantive Pushback & Specific Assumptions

We recommend against writing a full PRD at this stage. Instead, we must validate these four specific unvalidated assumptions:
1.  **Value Assumption:** Users prefer typing natural language prompts in a chat window over using standard keyword search and folder tags to find notes.
2.  **Viability Assumption:** The monthly API token cost of LLM inference is low enough to fit within our $8/month user subscription margins.
3.  **Feasibility Assumption:** We can index and retrieve 10,000+ notes dynamically without introducing UI lag or mobile app crashes.
4.  **Usability Assumption:** Users can write clear prompts that yield high-quality note summaries without encountering AI hallucinations.

---

## 3. 1-Week Discovery Plan & Falsifiable Kill Criteria

To validate these assumptions, we propose a 1-week discovery test before coding the backend:

| Discovery Activity | Metric / Goal | **Falsifiable Kill Criterion** |
| :--- | :--- | :--- |
| **Fake-Door Test** | Place an "AI Summarize" button in the note sidebar. Measure Click-Through Rate (CTR) over 7 days. | **KILL** the project if CTR is **< 8%** (anchored to 50% of our median entry-point CTR of 16% for other new features; we assume 8% is the minimum viable interest threshold to justify the API token cost - revisit after first measurement). |
| **Search Query Audit** | Analyze the database of searches. Count what percentage of queries are written in natural language (phrases) vs. single keywords. | **KILL** the project if natural language queries are **< 15%** of searches (anchored to 30% of our historical search queries; if less than half of this target segment writes in natural language, it indicates users think in keywords rather than conversational prompts). |
| **Willingness to Pay (Pre-Sale)** | Send an email campaign offering early beta access to AI features for a $5/month add-on fee. Measure signups. | **KILL** the project if add-on pre-orders are **< 3%** of our active customer base (anchored to our historical new add-on trial benchmark of 3%; absent internal data, we assume this baseline is required to cover LLM server and operations costs). |

---

## 4. [EVIDENCE-FREE DRAFT] Genuinely Minified Concept
*   **UI:** A static text drawer that slides in from the right when the "Summarize" button is clicked.
*   **Core Logic:** Feeds selected note text to the OpenAI GPT-4o API with a static system prompt to return a 3-bullet summary.
*   **Limits:** 5 summaries per user per day. No conversational history (no back-and-forth chat); no document generation.

---

## 5. CEO Positive Decision Framework

We should proceed with building a full version of this feature *only* if at least one of these strategic conditions is met:

1.  **Falsifiable Discovery Passes:** The fake-door CTR exceeds 12% AND pre-sale conversion exceeds 3%, demonstrating clear user demand and willingness to pay.
2.  **Contractual Expansion Revenue:** An enterprise prospect representing **>$150,000 ARR** signs a Letter of Intent (LOI) to subscribe, contingent *only* on the delivery of SOC2-compliant note summaries.
3.  **Monetization Strategic Pivot:** The board votes to pivot the company from a utility note tool to an enterprise knowledge-management agent, justifying a complete restructuring of our product roadmap.
