# Validation Scenario 6: Chatbot PRD Pushback (Adversarial)

This artifact represents the output of Workflow A under the `product-management` skill, applying the **License to Say No** when faced with evidence-free feature requests.

---

## 1. Context Gate Evaluation
*   **Strategy Context / ICP:** Not defined. The request is motivated by "competitors have it," not a validated need of our target ICP.
*   **Evidence Base:** **None**. There is zero telemetry data, customer support tickets, or user interview evidence showing our users want to chat with an AI bot in the note-taking app.
*   **Stage & Constraints:** Early-stage startup, limited engineering capacity.

---

## 2. License to Say No: Strategic Recommendation
> [!WARNING]
> **Recommendation: Run a 1-Week Discovery Phase First.**
> Building an AI chatbot is highly speculative and presents significant value and viability risks. We recommend running a lightweight, non-functional discovery test (such as a sidebar fake-door button or customer interviews) to validate demand before committing engineering resources.

Refer to the conflicts reference in `../product-management/references/conflicts.md#3-discovery-scale-continuous-discovery-vs-classic-mvp` to see the trade-offs of micro-discovery.

---

## 3. Minimal Draft [EVIDENCE-FREE DRAFT]

If leadership decides to proceed with initial validation, here is the minified draft of the shaped concept:

*   **Project Name:** AI Chatbot Assistant
*   **Appetite:** 2 weeks (Small Batch)
*   **Target Opportunity:** "I struggle to search and summarize my old notes." (Assuming this is the core value opportunity).
*   **Solution Boundary (Breadboard):** `[Sidebar Chat Link] -> (Click) -> [Chat Drawer] -> (Enter prompt) -> [Show AI note summary]`
*   **Explicit Out of Bounds:**
    *   No custom model fine-tuning (rely strictly on standard API endpoints).
    *   No collaborative chat history storage.
    *   No document-generation capabilities (restricted to reading and summarizing existing notes only).

### Four Product Risks of this Draft:
1.  **Value Risk (High):** Will users interact with a chatbot, or do they prefer standard search? We will test this by placing a mock "Chat with Notes" button in the UI and measuring Click-Through Rate.
2.  **Feasibility Risk (Medium):** Latency of note indexing and LLM API response times.
3.  **Viability Risk (High):** LLM API token costs. We must establish a daily token limit per user to avoid cost runaways.
4.  **Usability Risk (Medium):** LLM hallucinations or confusing chat box UI elements.
