---
name: apply-annotation-feedback
description: Apply structured review feedback from markdown annotations, inline comments, PR review comments, code comments, line-number notes, or document annotations. Use when the user asks to address annotations, apply review comments, resolve feedback, update only referenced files or sections, or incorporate reviewer notes without broad rewriting.
---

# Apply Annotation Feedback

Use this skill to turn review annotations into precise edits. The goal is to handle each actionable comment while preserving unrelated code and already-approved decisions.

## Trigger Examples

Use this skill when the user asks:

- "Apply these review comments."
- "Address the annotations in this Markdown."
- "Fix only the lines mentioned in the review."
- "Resolve this PR feedback."
- "Update the document based on these inline notes."
- "根据这些批注精确修改"

Do not use this skill for:

- A general code review where the user wants you to find issues.
- Broad rewriting or redesign without specific annotations.
- Feedback that is only conversational and does not request a change.
- Remote PR review workflows where a more specific GitHub skill is available and the user asks for GitHub thread inspection.

## Workflow

1. Collect the annotation sources:
   - User-provided Markdown comments, line notes, review summaries, PR comments, document annotations, or code comments.
   - Relevant files and line ranges referenced by the feedback.
2. Convert feedback into a short worklist:
   - Source or reviewer.
   - Target file, section, symbol, or line.
   - Requested change.
   - Status: actionable, needs confirmation, duplicate, already satisfied, or out of scope.
3. Inspect the target context before editing.
4. Apply the smallest change that satisfies each actionable annotation.
5. Preserve unrelated text, formatting, code style, and behavior.
6. Run focused validation for changed code or documents.
7. Report each annotation as done, skipped, already satisfied, or needs confirmation.

## Result Format

Use a concise status table when there are multiple comments:

```markdown
| Feedback | Target | Status | Notes |
| --- | --- | --- | --- |
| <short label> | `<file or section>` | Done | <what changed> |
```

Then include:

- Changed files.
- Verification commands and results.
- Any feedback that needs user confirmation.

## Decision Rules

- Treat annotations as scoped instructions, not permission for broad refactors.
- If a comment conflicts with another comment, current requirements, or project conventions, pause and ask or mark it as needing confirmation.
- If the referenced code has moved, locate the current equivalent before deciding the comment is stale.
- If a comment requests an unsafe or behavior-changing edit, explain the risk before applying it.
- If the feedback is already satisfied, do not create a cosmetic diff just to show activity.
- Do not mark remote review threads resolved, reply to reviewers, or submit forms unless the user explicitly asks.
- When applying document feedback, preserve the author's voice unless the annotation asks for tone changes.

## Validation

Before finishing:

- Check that every annotation has a recorded status.
- Re-read the edited lines or sections against the original feedback.
- Run the narrowest relevant test, lint, typecheck, render, or document check.
- Run `git status --short` when editing repository files.
- Report any skipped validation and why it was skipped.
