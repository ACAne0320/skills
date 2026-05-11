---
name: write-handoff-prompt
description: Create a self-contained handoff for another coding agent to continue the current session's work. Use when the user asks to write a prompt for another session or agent to take over, continue work elsewhere, switch sessions, summarize current progress for handoff, or let a fresh agent pick up without asking the user for repeated context.
---

# Write Handoff Prompt

Use this skill to create a durable handoff for a fresh coding-agent session. Prefer writing a Markdown handoff file in the workspace, then provide a short prompt that tells the next agent to read it and continue.

## Trigger Examples

Use this skill when the user asks to:

- "Write a prompt for the next agent to take over"
- "Generate a handoff prompt"
- "让下一个代理继续这个任务"
- "生成交接 prompt"
- "Summarize this session so another coding agent can continue"
- "Write a handoff for a fresh session"

Do not use this skill for:

- General conversation summaries that are not meant for task continuation.
- User-facing release notes, changelogs, or progress reports.
- Archiving a finished task when no follow-up agent needs to continue.

## Workflow

1. Confirm the user wants a handoff for a new coding-agent session.
2. Inspect current workspace state before writing the handoff:
   - Current working directory.
   - Git branch, recent commits, and `git status --short`.
   - Relevant changed files and important diff summaries.
   - Running processes, servers, tests, or tools that matter for continuation.
3. Reconstruct the task context:
   - User's original goal.
   - Latest user instructions.
   - Decisions already made.
   - Work completed.
   - Work still pending.
   - Blockers, risks, assumptions, and things not to repeat.
4. Write a Markdown handoff file at `handoffs/YYYY-MM-DD-<topic>.md` unless the user requests another path.
5. Include enough detail for a fresh agent with repository access to continue without asking the user for repeated context.
6. Final response: give the handoff file path and a short copyable prompt for the next session.

## Handoff File Format

Use this structure unless the task needs a small adjustment:

```markdown
# Handoff: <topic>

## Next Agent Prompt

You are continuing work in this repository. First read this handoff file completely, then continue from the "Next Steps" section. Do not ask the user for repeated context unless this handoff explicitly marks something as unknown.

## User Goal

<What the user ultimately wants.>

## Latest User Instructions

<Most recent instructions that should guide the next agent.>

## Workspace State

- Working directory: `<absolute path>`
- Branch: `<branch or unknown>`
- Recent commit: `<commit or no commits yet>`
- Git status summary:

```text
<git status --short output>
```

## Completed Work

- <Concrete completed item with file paths when useful.>

## Current Changes

- `<path>`: <what changed and why>

## Important Context

- <Decision, constraint, convention, or user preference the next agent must preserve.>

## Verification

- Ran: `<command>`
- Result: <pass/fail/skipped and key output>

## Next Steps

1. <Immediate next action.>
2. <Following action.>
3. <Validation or finalization action.>

## Risks And Unknowns

- <Anything uncertain, risky, or intentionally deferred.>

## Do Not Repeat

- <Work already done or approaches that should not be retried.>
```

## Decision Rules

- If the handoff is small, keep the file concise and still include every section.
- If the handoff is large, prefer detailed file sections over compressing everything into the chat response.
- If the next agent needs command output, include the important excerpts rather than vague statements.
- If a fact is uncertain, label it as unknown instead of guessing.
- If the user explicitly asks for a prompt only, produce a self-contained prompt in chat and do not create a file.
- If there are uncommitted changes, preserve them in the handoff and avoid changing unrelated files.

## Validation

Before finishing:

- Re-read the handoff file after writing it.
- Run `git status --short` to confirm the handoff file appears as expected and no unintended files changed.
- Check that the final short prompt points to the correct handoff path.
- Ensure a fresh agent can identify the next action without asking the user to restate context.

## Final Response Format

Keep the final response short:

```text
Created the handoff at `<path>`.

Use this prompt in the new session:

<short prompt>
```
