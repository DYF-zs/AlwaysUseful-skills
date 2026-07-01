---
name: analyze-product-mvp
description: Product-management workflow for turning a product goal, business scenario, demo idea, platform capability question, or AI/agent feature concept into a Markdown MVP analysis document. Use when Codex needs to research or reason through product flows, draw scenario flows, abstract a real runnable MVP loop, split capabilities by ownership such as platform existing/platform needs/customer-owned, audit whether a capability table supports the MVP, or produce a PM-style feature/capability breakdown.
---

# Analyze Product MVP

Use this skill to produce a PM analysis document from a goal or scenario. The default output is Markdown. Do not default to HTML or slides.

## Workflow

1. Clarify the goal only when necessary.
   - Identify product, users, scenarios, audience, and output format.
   - If the prompt is broad but workable, proceed with explicit assumptions instead of over-questioning.
   - Ask at most 1-3 high-impact questions when missing information would change the MVP boundary.

2. Build the scenario flow.
   - Identify actors: end user, platform, customer systems, third-party services, operators/humans.
   - Describe the core user journey before listing features.
   - Add Mermaid only when the flow has multiple actors, system states, branching, or handoff.

3. Define the MVP loop.
   - MVP means a real runnable minimum, not a static page demo.
   - Mark "MVP required" only when removing the capability breaks the minimum flow.
   - Separate "nice product experience" from "flow cannot run."

4. Split capabilities by ownership.
   - If the user did not specify a model, default to:
     - L1: Existing platform capability can be reused directly.
     - L2: Platform should add or extend reusable product capability.
     - L3: Customer business system, content platform, model strategy, or third-party service owns it.
   - Grade by ownership, not implementation difficulty.
   - If a capability may require deep platform refactoring but still belongs to the platform, keep it in L2.

5. Write capability rows at action-result granularity.
   - Each row should say what is clicked/triggered, what the system does, and what the user or operator sees.
   - Avoid vague nouns like "support workflow" without observable behavior.
   - Remove capabilities that are not needed for the stated scenario, even if adjacent products commonly have them.

6. Audit the result.
   - Verify the MVP loop can be walked end-to-end.
   - Verify every MVP-required item appears in the capability tables.
   - Verify non-MVP rows do not distract from the target scenario.
   - Include a short conclusion and a small statistics table when useful.

## References

- Use `references/output-template.md` when asked to create a full Markdown document.
- Use `references/grading-models.md` when the capability split is ambiguous or the user requests another grading model.
- Use `references/agent-omnichannel-example.md` only as a compact example for agent, communication, customer-service, companion, or platform-vs-customer ownership tasks.

## Output Rules

- Prefer Chinese output when the user writes in Chinese.
- Use concrete scenario language instead of generic product jargon.
- Do not invent static placeholder data as if it were a real dependency; for real MVPs, describe real service/API integration boundaries.
- Keep final documents structured, with tables for MVP steps and capabilities.
- If reviewing an existing table, lead with whether the MVP loop is complete, then list gaps, over-scoped items, and recommended changes.
