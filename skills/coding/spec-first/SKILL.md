---
name: spec-first
description: Create a concrete implementation spec before coding medium, large, risky, or ambiguous development work. Use when the user asks to plan a feature, write a PRD or technical spec, clarify requirements before implementation, prevent direct coding, define goals, constraints, data model, APIs, edge cases, test plan, or says to work spec-first.
---

# Spec First

Use this skill to turn an unclear or risky coding request into an implementable spec before code changes begin. The goal is to make the work testable, bounded, and reviewable.

## Trigger Examples

Use this skill when the user asks:

- "Write the spec first, then we can implement."
- "Before coding, clarify the requirements and plan."
- "Create a technical spec for this feature."
- "Help me turn this rough idea into an implementation plan."
- "Do not start coding yet; define the behavior and tests."
- "先写规格, 不要直接实现"

Do not use this skill for:

- Tiny edits where the requested behavior and file are already obvious.
- Pure code review where the user wants findings rather than a spec.
- A task with an already accepted spec where the user asks to implement it.
- Exploratory brainstorming when no concrete implementation target exists.

## Workflow

1. Identify the feature, bug, refactor, or system behavior being specified.
2. Inspect the repository enough to ground the spec:
   - Project instructions such as `AGENTS.md`, `README.md`, or equivalent.
   - Relevant entry points, routes, APIs, types, data models, tests, and docs.
   - Existing patterns for naming, validation, error handling, and testing.
3. Separate confirmed facts from assumptions.
4. Draft the spec using the output structure below.
5. Ask only for blocking information. If a reasonable assumption is safe, label it and continue.
6. Stop after the spec unless the user explicitly asks to proceed with implementation.

## Output Structure

Use this structure unless the task clearly needs a smaller version:

```markdown
## Objective

<What should be true when this work is done.>

## Context

<Relevant existing behavior, files, constraints, and user intent.>

## Requirements

- <Concrete behavior or capability.>

## Non-Goals

- <What this work should not attempt.>

## Current Behavior

<What the system does now, with file references when available.>

## Proposed Behavior

<What should change from a user, API, or system perspective.>

## Affected Surfaces

- UI:
- Routes / APIs:
- Data model / types:
- Tests:
- Docs / config:

## Edge Cases

- <Failure modes, empty states, permissions, concurrency, migration, compatibility, or rollback concerns.>

## Test Plan

- <Unit, integration, e2e, manual, or regression checks.>

## Implementation Plan

1. <Small ordered step.>

## Open Questions

- <Question, or "None".>
```

## Decision Rules

- Treat the spec as a contract for implementation, not a motivational outline.
- Prefer the smallest spec that makes the work safe to implement.
- Do not invent product decisions, public API changes, migrations, deadlines, or success metrics. Mark them as assumptions or open questions.
- If the request touches public APIs, data schemas, auth, billing, permissions, or irreversible data changes, call those risks out explicitly.
- If the best approach depends on a fast-moving library, framework, API, or standard, verify with primary sources before presenting it as current.
- If the user asks for a PRD, keep user outcomes and acceptance criteria visible. If the user asks for a technical spec, emphasize interfaces, data flow, and validation.
- Do not edit production code during this skill unless the user explicitly changes the request from planning to implementation.

## Validation

Before finishing:

- Confirm each requirement has at least one validation step.
- Confirm every proposed code surface is tied to a current file, module, or clearly marked assumption.
- Confirm blockers are named as open questions rather than hidden in vague language.
- Confirm the implementation plan can be executed in small, reviewable steps.
