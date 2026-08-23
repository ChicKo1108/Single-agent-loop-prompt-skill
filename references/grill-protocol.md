# Atomic Grill Protocol

## Purpose

Help the user think through the real task before encoding automation. This is collaborative requirements discovery, not a disguised solution.

## Question discipline

- Run 10–20 conversational rounds unless the user explicitly says they are ready or asks to skip ahead.
- Ask one atomic, decision-sized question each round. Two are allowed only when answering one without the other would mislead.
- Start with outcome and stakes; move through evidence, authority, risks, budgets, records, and handoff.
- Do not ask for facts that can be safely discovered from context or read-only inspection.
- Test vague answers with a concrete counterexample or failure scenario.
- Surface conflicting answers and ask the user to choose; never silently reconcile them.
- Explain why the current choice matters in one or two sentences, including the main tradeoff.
- Offer examples as illustrations, not predetermined answers.
- Never request passwords, private keys, full tokens, or secrets. Ask how credentials will be supplied securely.

## Adaptive question map

Use this as coverage guidance, not a fixed questionnaire. Skip resolved areas and deepen unclear or high-risk areas.

1. Outcome: What observable state means done?
2. Motivation: What failure or opportunity makes this valuable?
3. Stakeholders: Who decides whether it is acceptable?
4. Scope: What is included and explicitly excluded?
5. Source of truth: Which system, dataset, repository, document, or person is authoritative?
6. Starting state: What is known, suspected, and unknown?
7. Acceptance: Which checks are mandatory, and which are preferences?
8. Evidence: What proof must support each conclusion?
9. Loop unit: What counts as one iteration or experiment?
10. Evaluation: Who or what scores an iteration, and at what threshold?
11. Permitted actions: What may the agent change autonomously?
12. Approvals: Which external, costly, irreversible, or high-impact actions need confirmation?
13. Protected assets: What must never be deleted, overwritten, exposed, or interrupted?
14. Rollback: How should failed changes be reversed?
15. Budgets: What are the time, iteration, cost, rate, or resource limits?
16. Retries: Which failures are transient, and how many retries are allowed?
17. Blocked state: What must be reported when the agent cannot continue?
18. Observability: Where should records live, at what detail, and for how long?
19. Resume semantics: How should a later run discover completed work and continue safely?
20. Handoff: What should the final summary enable the next human or agent to do?

## Decision ledger

Maintain a compact ledger:

| Area | Decision | Confidence | Open issue |
|---|---|---:|---|
| Outcome | … | high/medium/low | … |

Reflect it after roughly every 4–6 rounds or when a contradiction appears. Do not create files during clarification unless asked.

## Readiness test

The task is ready only when success is independently checkable, at least one bounded failure terminal state exists, authority and protected assets are clear, each iteration produces decision-changing evidence, record/resume behavior is defined, and remaining assumptions are accepted.

If the user says “I have thought it through,” stop the remaining rounds, summarize missing decisions as assumptions, and ask for one confirmation. Respect a direct request to draft immediately.
