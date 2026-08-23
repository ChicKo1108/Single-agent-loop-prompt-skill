---
name: single-agent-loop-prompt
description: Generate robust single-agent loop prompts for iterative tasks in any domain. Use when an agent should keep diagnosing, creating, evaluating, or improving until explicit acceptance criteria pass, especially when the prompt needs atomic clarification, bounded retries, approval boundaries, per-loop records, and a final summary. Do not use merely to execute an already-complete loop prompt.
---

# Single-Agent Loop Prompt

Create an outcome-first prompt that lets one agent iterate autonomously without becoming unbounded, destructive, or unverifiable.

## Workflow

### 1. Establish the operating context

Identify what will run the prompt, its tools, writable storage, approval mechanism, budgets, and whether it can resume across sessions. Do not assume shell, Git, browser, filesystem, or network access.

### 2. Grill before drafting

Read [references/grill-protocol.md](references/grill-protocol.md) and conduct the clarification interactively.

- Ask 10–20 rounds of atomic questions by default.
- Ask one decision-sized question per round; use at most two only when inseparable.
- Adapt each next question to the previous answer instead of presenting a static questionnaire.
- Briefly explain the consequence or tradeoff behind each question.
- Maintain a compact decision ledger and periodically reflect it back for correction.
- Do not draft the final Loop prompt during this phase.
- End early only if the user explicitly says they have thought it through or asks to skip ahead. Surface remaining assumptions and obtain confirmation before drafting.

### 3. Pass the readiness gate

Before drafting, verify that these are sufficiently defined:

- target outcome and excluded scope;
- initial state, inputs, and source of truth;
- observable acceptance criteria and verification methods;
- permitted actions, gated actions, protected assets, and rollback;
- Loop unit, retry policy, budgets, and stopping rules;
- record location, retention, redaction, and final deliverables;
- behavior when blocked, interrupted, or resumed.

Present a concise requirement brief containing decisions, assumptions, open items, and contradictions. Ask the user to confirm it. Draft only after confirmation unless the user explicitly delegates remaining decisions.

### 4. Generate the Loop prompt

Read [references/loop-prompt-template.md](references/loop-prompt-template.md) and adapt it to the actual domain. Preserve the user's terminology and constraints. Remove generic sections that do not change execution.

The prompt must define a closed Loop with observation, one current hypothesis or improvement target, the smallest useful action, objective validation, recorded evidence, and an explicit transition to continue, escalate, roll back, succeed, or stop safely.

Define both success and non-success terminal states. Never use “until perfect,” “keep trying forever,” or another criterion that cannot be evaluated.

### 5. Require durable records

Read [references/run-recording.md](references/run-recording.md). Require one summary file per Loop, one checkpoint file per important result outside a Loop, and a continuously updated `summary.md`. Include redaction, atomic writes where practical, and a fallback when files cannot be written.

Keep records proportional to the task. Prefer bounded evidence and summaries over unlimited raw logs.

### 6. Deliver and self-review

Return the confirmed requirement brief, copy-ready Loop prompt, a short explanation of terminal and authorization behavior, and remaining customizable assumptions.

Before delivery, check that the prompt cannot falsely claim success, silently expand scope, retry indefinitely, overwrite protected assets, leak secrets, or finish without producing `summary.md`.
