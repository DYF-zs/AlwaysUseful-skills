# Agent + Omnichannel Reference Example

Use this only as a compact example for AI agent, communications, customer-service, companion, or platform/customer boundary tasks.

## Principle

An MVP is a real runnable minimum, not a static demonstration. It should use real users, credentials, services, server-side flows, and real customer or provider APIs where the scenario depends on them.

Grade by ownership:

- **L1**: existing communication/platform capability.
- **L2**: communication/platform should add a reusable agent capability.
- **L3**: customer business system, content platform, model strategy, or third-party service owns it.

## Customer Service Agent MVP Loop

1. User enters from an order, after-sales, or support entry.
2. System creates or reuses a service Conversation by `userId + businessSessionId`.
3. Platform creates the conversation under system ownership and adds user + AI agent.
4. User sends a message.
5. Server reliably triggers Agent orchestration.
6. Agent reads recent history and business context, then generates a reply.
7. Server sends the reply as the bound AI user into the same Conversation.
8. If escalation is needed, handoff starts and a human joins the same Conversation.
9. Service ends by archiving the Conversation and preserving history.

Typical required ownership split:

- L1: conversation container, text message send/receive, history read, archive/delete, human member message.
- L2: AI user binding, system-owned conversation creation, business-session reuse, server-side message trigger, idempotency, trusted AI send, AI session state, AI orchestration layer, handoff start.
- L3: order/logistics/after-sales API, intent/entity extraction, customer service rules.

## Companion Agent MVP Loop

1. User enters a character chat entry.
2. System creates or reuses a long-lived Conversation by `userId + agentId`.
3. Conversation/member metadata stores character profile/persona references.
4. User sends a text message.
5. Server triggers character Agent orchestration.
6. Agent streams a reply as the bound AI user.
7. Final reply is written to Conversation history.
8. User can leave and later restore the same active/hibernated Conversation.

Typical required ownership split:

- L1: conversation container, text message send/receive, final message display, recent history read.
- L2: AI character binding, `userId + agentId` reuse, profile reference fields, trusted AI send, server trigger, idempotency, AI session state, model orchestration, streaming display, stream completion persistence, hibernation/recovery.
- L3: persona and response style. Long-term memory, relationship growth, proactive recall, voice orchestration, compliance policy are not required for the minimum text companion loop unless the user explicitly includes them.

## Common Review Checks

- If "trusted AI send" is absent, the flow is not production-safe.
- If server-side trigger is absent, the flow is only a client-driven demo.
- If idempotency is absent, repeated callbacks can duplicate agent replies.
- If customer data/tool calls are required by the scenario, keep them L3; do not move them into the platform.
