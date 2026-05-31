---
name: curate-agent-memory
description: Curate durable coding-agent instructions in AGENTS.md, CLAUDE.md, cursor rules, or similar project memory files. Use when the user asks to update agent memory, record a repeated lesson, add persistent project rules, consolidate agent instructions, prevent future agents from repeating a known mistake, or decide whether a lesson belongs in project rules.
---

# Curate Agent Memory

Use this skill to add or revise durable agent instructions without letting memory files become noisy. The goal is to preserve rules that future agents can execute reliably.

## Trigger Examples

Use this skill when the user asks:

- "Update AGENTS.md so future agents do not repeat this."
- "Should this lesson become project memory?"
- "Add a persistent rule for coding agents."
- "Clean up our agent instructions."
- "Record this in CLAUDE.md / cursor rules."
- "把这个教训沉淀到 AGENTS.md"

Do not use this skill for:

- One-off task summaries or handoffs. Use `write-handoff-prompt` for that.
- Temporary commands, local machine quirks, or context that will expire soon.
- Secrets, credentials, private tokens, personal data, or hidden reasoning.
- Preferences that are not stable enough to guide future work.
- Automatically recording every mistake without user intent.

## Workflow

1. Identify the memory target:
   - `AGENTS.md`, `CLAUDE.md`, `.cursor/rules`, `.github/copilot-instructions.md`, or another file named by the user.
   - Prefer the most local project-level instruction file that future agents will actually read.
2. Inspect existing instructions before proposing changes.
3. Extract candidate lessons from the user's request, recent failure, review feedback, or repeated pattern.
4. Apply the durability filter:
   - Repeated or likely to recur.
   - Project-specific or workflow-specific.
   - Stable over time.
   - Actionable by an agent.
   - Short enough to remember and enforce.
   - Not already covered by existing instructions.
5. Edit the smallest relevant section, merging with existing rules rather than appending duplicates.
6. Use imperative wording that tells future agents exactly what to do or avoid.
7. Re-read the edited section and check for conflicts or stale language.

## Memory Rule Shape

Prefer rules that look like this:

```markdown
- When <specific situation>, <specific action>. <Optional short reason or exception.>
```

Good memory rules:

- Name the trigger condition.
- Give an observable action.
- Include exceptions only when they prevent misuse.

Weak memory rules:

- "Be careful."
- "Use good engineering judgment."
- "Remember what happened last time."
- Long narratives that future agents must reinterpret.

## Decision Rules

- If the lesson is a task continuation detail, write a handoff instead of memory.
- If the lesson is a personal preference, keep it out of project rules unless the user explicitly wants it there.
- If the rule applies across all repositories, ask before editing global agent memory.
- If no suitable instruction file exists, create one only when the user asked for persistent memory or the repository convention clearly expects it.
- If a proposed rule conflicts with existing instructions, surface the conflict before editing.
- Prefer one precise rule over a broad checklist.
- Do not add background essays, changelogs, or explanations of the conversation that produced the rule.

## Validation

Before finishing:

- Confirm the new or revised rule is actionable, stable, and not duplicated.
- Confirm the target file is one future agents are likely to read.
- Run `git diff -- <memory-file>` or otherwise inspect the final change.
- Report the exact rule added or revised and any candidate lessons intentionally left out.
