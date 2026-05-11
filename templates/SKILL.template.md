---
name: skill-name
description: Describe what this skill does and the exact situations that should trigger it. Include both the capability and the user requests, file types, tools, or workflows that should activate it.
---

# Skill Name

Use this skill to [specific outcome]. Keep this file concise: put only the workflow and non-obvious guidance here, and move long examples or detailed reference material into `references/`.

## Trigger Examples

Use this skill when the user asks to:

- "[example request that should trigger this skill]"
- "[another trigger phrased like a real user request]"

Do not use this skill for:

- "[similar-looking request that belongs elsewhere]"
- "[out-of-scope task]"

## Workflow

1. Confirm the task fits this skill's scope.
2. Inspect the relevant project files, user-provided artifacts, or external context.
3. Load only the specific resource files needed for this request.
4. Execute the workflow using the rules below.
5. Validate the result with the listed checks before reporting completion.

## Decision Rules

- If [condition], do [action].
- If [condition], read `references/[file].md` before proceeding.
- If the request needs deterministic or repeated processing, prefer `scripts/[script].*` over rewriting one-off code.
- If required context is missing and a reasonable assumption would be risky, ask one concise question.

## Resources

- `scripts/`: reusable automation or deterministic helpers. Run them instead of retyping fragile logic.
- `references/`: detailed documentation loaded only when needed. Mention when each file should be read.
- `assets/`: templates or source assets used in final outputs. Do not load these into context unless inspection is needed.

## Validation

Before finishing:

- Run `[validation command]` when files or scripts are changed.
- Check that [expected output or behavior] is true.
- Report any skipped validation and why it was skipped.

## Boundaries

- Do not add broad background material that Codex already knows.
- Do not create extra documentation files unless they directly support the skill.
- Do not load every reference file by default; use progressive disclosure.
- Keep instructions imperative, concrete, and easy to scan.

## Author Notes

Remove this section after creating a real skill:

- Use lowercase hyphen-case for `name`.
- Make `description` the primary trigger surface; the body is loaded only after the skill is selected.
- Keep `SKILL.md` under about 500 lines.
- Prefer concise examples over long explanations.
