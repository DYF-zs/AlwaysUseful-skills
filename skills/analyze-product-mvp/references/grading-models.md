# Capability Grading Models

Choose one grading model per document. If the user does not specify, use the ownership model.

## Ownership Model (Default)

Use when analyzing platform products, SDKs, APIs, SaaS capabilities, or customer integration boundaries.

- **L1: Existing platform capability**
  - Already available or directly reusable.
  - May require page wiring, configuration, or normal integration.
  - Does not require new reusable platform product capability.

- **L2: Platform addition or extension**
  - Belongs in the platform as reusable capability.
  - Requires new API, state, event, storage, permission, UI contract, orchestration, or service behavior.
  - Use L2 even if implementation might be deep, as long as ownership is platform-side.

- **L3: Customer or external capability**
  - Belongs to customer business systems, content platforms, model prompts, knowledge bases, workflows, third-party services, operations, or policy.
  - Platform may store references, pass messages, or carry results, but does not own the logic.

## Priority Model

Use when the user asks for roadmap or delivery phases.

- **P0**: must exist or the MVP cannot run.
- **P1**: important for a credible beta or first customer rollout.
- **P2**: useful enhancement, optimization, or later productization.

## Implementation Layer Model

Use when the user asks for engineering ownership.

- **Frontend**: page, state, rendering, user action, input, display.
- **Backend/platform**: APIs, storage, permissions, orchestration, events.
- **Customer system**: business data, rules, workflows, operations.
- **Third party**: external provider, model, payment, logistics, identity, etc.

## MVP Required Policy

Mark "MVP Required = Yes" only when removing the capability breaks the minimum real runnable flow.

Mark "No" when:

- the user can still complete the core job without it;
- it improves observability, UX, resilience, or operational quality but does not block the loop;
- it is a full-product feature outside the stated scenario;
- it belongs to future commercialization rather than first runnable MVP.

Do not mark a capability "No" merely because it is hard. Difficulty is not ownership or MVP necessity.
