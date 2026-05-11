---
name: review-implementation-options
description: Review a coding change or implementation direction by comparing minimum-change, clean-refactor, best-practice, and alternative approaches. Use when the user asks what the smallest safe change is, what the cleanest or most elegant thorough solution is, whether there are better ideas, what industry best practice would be, or how to evaluate competing implementation options.
---

# Review Implementation Options

Use this skill to evaluate implementation choices after or during development. Focus on trade-offs, not just defects. The goal is to help the user decide whether to keep the current change, make a small adjustment, refactor more deeply, or choose a different design.

## Trigger Examples

Use this skill when the user asks:

- "What are the minimum-change and cleanest thorough options here?"
- "Is there a more elegant way to implement this?"
- "What would the industry best practice be?"
- "Besides this approach, are there other ideas?"
- "Review this implementation direction."
- "Should I do the small patch or a deeper refactor?"

Do not use this skill for:

- Security, correctness, or regression-focused code review where findings should lead.
- Generic brainstorming before code or requirements exist.
- Implementation work where the user already chose a specific approach and asked you to edit files.

## Workflow

1. Identify the change, file, feature, bug, or design decision under review.
2. Inspect the relevant code, tests, docs, and local conventions before judging.
3. If there are existing changes, inspect the diff and separate user changes from your own.
4. Infer the real constraint: speed, risk, maintainability, compatibility, performance, team convention, or long-term architecture.
5. Compare approaches using the output structure below.
6. Recommend one approach and state the condition under which that recommendation would change.

## Output Structure

Use concise sections:

```markdown
## Context

<What is being evaluated and what constraints matter.>

## Option 1: Minimum Change

- Scope: <files or behavior touched>
- What it does: <short description>
- Pros: <why this is attractive>
- Cons: <what debt or risk remains>
- Validation: <tests or checks>

## Option 2: Clean Refactor

- Scope: <files or behavior touched>
- What it does: <short description>
- Pros: <why this is cleaner>
- Cons: <cost, risk, migration burden>
- Validation: <tests or checks>

## Option 3: Best-Practice / Long-Term

- Scope: <files or behavior touched>
- What it does: <short description>
- Pros: <why this aligns with durable design>
- Cons: <when this is overkill>
- Validation: <tests or checks>

## Other Viable Ideas

- <Alternative approach and when it fits.>

## Recommendation

<Pick one, explain why, and name the trigger that would make another option better.>
```

Omit a section only when it truly does not apply, and say why.

## Decision Rules

- Lead with the option that best matches the user's current constraint, then compare the others.
- Treat "minimum change" as the smallest change that is still correct and testable, not the smallest textual diff at any cost.
- Treat "cleanest" as simpler boundaries, clearer ownership, better tests, and less future surprise; avoid elegance that only makes the code clever.
- Treat "best practice" as context-dependent. Prefer the project's existing conventions and official docs over generic advice.
- If the best-practice answer depends on a fast-moving framework, library, or standard, verify with primary sources before claiming it.
- If you cannot inspect the relevant code, state the assumption and give a conditional review instead of pretending certainty.
- Do not make code edits unless the user explicitly asks to implement one of the options.

## Review Criteria

Consider these dimensions when relevant:

- Correctness and regression risk.
- Blast radius and migration cost.
- Fit with existing architecture and naming conventions.
- Testability and observability.
- Performance, accessibility, security, and compatibility.
- Long-term maintainability and how easy the next developer can reason about it.
- Whether the change preserves user intent and current behavior.

## Validation

Before finishing:

- Cite concrete files, functions, or diffs when available.
- Make the trade-off explicit for each option.
- Include at least one verification step for the recommended approach.
- Avoid vague recommendations like "refactor it" without naming the actual boundary or module to change.
