---
name: tdd-vertical-slice
description: Implement coding work through small test-driven vertical slices. Use when the user asks to build or modify functionality incrementally, add a failing test first, avoid broad rewrites, work one behavior at a time, use TDD, make minimal implementation changes, or keep a feature implementation disciplined and verifiable.
---

# TDD Vertical Slice

Use this skill to implement functionality in small, tested slices. Each slice should prove one behavior, add the minimum code needed, and leave the project in a verifiable state before moving on.

## Trigger Examples

Use this skill when the user asks:

- "Implement this with TDD."
- "Build it one vertical slice at a time."
- "Add a failing test first, then make it pass."
- "Do not rewrite everything; move in small tested steps."
- "Implement the next behavior and verify it."
- "用 TDD 小步实现"

Do not use this skill for:

- Pure planning or architecture review before implementation starts.
- Formatting-only changes.
- Tasks where the user explicitly asks for a quick one-shot prototype.
- Repositories with no practical test surface, unless the user still wants a disciplined manual-check slice.

## Workflow

1. Inspect repository state:
   - Run `git status --short`.
   - Identify relevant project instructions and test commands.
   - Note user changes and avoid overwriting them.
2. Confirm the target behavior is clear enough to test. If not, use or request a spec first.
3. Choose the smallest vertical slice:
   - Prefer one user-visible behavior, API behavior, state transition, or regression.
   - Include all layers needed for that behavior, but no unrelated cleanup.
4. Write or update a focused failing test.
5. Run the narrow test and confirm it fails for the expected reason.
6. Implement the minimum code needed to pass.
7. Run the narrow test again.
8. Refactor only within the slice when the test is green.
9. Repeat for the next slice only when it is still within the user's requested scope.
10. Run broader relevant checks before finishing.

## Slice Report Format

Track progress in the final response or working notes:

```markdown
## Slices

1. <Behavior>
   - Test: <command and expected failure before fix>
   - Implementation: <files changed>
   - Result: <passing command>

## Final Verification

- <Command>: <result>
```

## Decision Rules

- Keep each slice independently reviewable.
- A vertical slice may touch multiple layers, but only for one behavior.
- Do not batch unrelated tests or refactors into the same slice.
- If an existing test already captures the behavior, update or use it instead of adding duplicate coverage.
- If no automated test can be written at reasonable cost, explain why and define a focused manual or runtime verification before editing.
- If the first failing test reveals the spec is wrong or ambiguous, pause and resolve that ambiguity before continuing.
- If changes begin to require a broader architecture shift, stop and recommend `architecture-boundary-review` rather than pushing through.

## Validation

Before finishing:

- Confirm at least one focused test or verification proves each completed behavior.
- Run the relevant broader test, lint, typecheck, build, or manual check when appropriate.
- Run `git status --short` and confirm only intended files changed.
- Report skipped checks and why they were skipped.
