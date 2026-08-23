# Durable Run Recording

## Default layout

When the executing agent can write files, embed this adaptable layout:

```text
<record-root>/<run-id>/
├── 00-brief.md
├── 01-baseline.md
├── loops/
│   ├── loop-001.md
│   └── ...
├── checkpoints/
│   ├── <timestamp>-<event>.md
│   └── ...
├── evidence/
│   └── <bounded supporting artifacts>
├── manifest.md
└── summary.md
```

Choose `<record-root>` with the user. Prefer a task-local ignored directory such as `.agent-runs/` for software projects, or a user-designated workspace in other domains. Do not commit operational records unless explicitly requested.

Use a sortable run ID such as `YYYYMMDD-HHMMSS-short-task-name`. On resume, reuse the existing run directory unless the user requests a new run.

## Per-Loop file

Write a file after every completed iteration, including no-change iterations:

```markdown
# Loop NNN — <short title>

- Started:
- Finished:
- Objective:
- Starting evidence:
- Current hypothesis or candidate:
- Action taken:
- Changed artifacts:
- Validation performed:
- Result: pass | fail | partial | blocked | rolled-back
- Evidence references:
- What was learned:
- Decision:
- Next action:
- Budget consumed / remaining:
```

Do not dump unlimited output into the Loop file. Save only bounded supporting evidence and reference it. Include exact commands only when reproducibility or auditability matters.

## Checkpoint file

Create a checkpoint immediately when an important result should survive interruption, including a confirmed root cause, passed or regressed acceptance criterion, approval boundary, rollback, unavailable dependency, security/privacy/compliance/data-integrity risk, changed source of truth, block, or resume.

```markdown
# Checkpoint — <event>

- Time:
- Event:
- Evidence:
- Impact:
- Decision:
- Required follow-up:
```

## `summary.md`

Create `summary.md` before the first action, then update it atomically after every Loop and checkpoint. It is the authoritative current conclusion, not merely the final report.

```markdown
# Run Summary

## Status
in-progress | succeeded | blocked | stopped | failed-safely

## Objective

## Current conclusion

## Acceptance criteria
| Criterion | State | Evidence |
|---|---|---|

## Work completed

## Changes currently in effect

## Important decisions

## Risks and protected assets

## Remaining work or blocker

## Resume instructions

## Final handoff
- Final result:
- Evidence:
- Changed artifacts:
- Rollback path:
- Follow-up:
```

Never mark `succeeded` until every mandatory criterion has current evidence. A blocked or failed-safe result is a valid terminal conclusion and must be recorded plainly.

## Manifest, atomicity, and redaction

Use `manifest.md` to list record files, their purpose, and relevant source artifacts. Store only evidence needed to reproduce or audit conclusions.

Redact credentials, tokens, private keys, personal data, proprietary inputs, and sensitive environment values. Record that a credential check passed without recording its value.

Prefer write-to-temporary-then-rename when supported so interruption cannot leave `summary.md` half-written.

## No-filesystem fallback

If the agent cannot write files, require clearly labeled virtual artifacts after every iteration:

```text
FILE: loops/loop-001.md
<content>

FILE: summary.md
<updated content>
```

The outer harness or user must persist them. Do not claim durable observability unless something actually stores the artifacts.

