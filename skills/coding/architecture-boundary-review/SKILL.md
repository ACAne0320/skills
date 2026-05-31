---
name: architecture-boundary-review
description: Review existing code architecture and model implementation boundaries before large changes, refactors, or new modules. Use when the user asks to critique design, inspect coupling, map public APIs, call graph, data flow, production and test adapters, leaking abstractions, module ownership, or decide what should and should not change before coding.
---

# Architecture Boundary Review

Use this skill to inspect the current design before changing it. Focus on how the code is shaped today, where boundaries are unclear, and what direction would reduce future risk.

## Trigger Examples

Use this skill when the user asks:

- "Review the architecture before we implement this."
- "Tell me where the design is wrong before refactoring."
- "Map the public APIs, call graph, and data flow first."
- "What boundaries should this module have?"
- "Where is the coupling or abstraction leak?"
- "先审查架构边界, 不要急着写代码"

Do not use this skill for:

- Generic code review where findings should focus on bugs and regressions.
- Comparing several already-defined implementation options. Use `review-implementation-options` for that.
- Tiny local changes that do not affect module boundaries.
- Implementation work where the user already chose a concrete design and asked for edits.

## Workflow

1. Identify the module, feature, subsystem, or refactor target.
2. Inspect current code before judging:
   - Entrypoints, public APIs, exported types, routes, commands, jobs, or UI surfaces.
   - Core data structures and state transitions.
   - Call graph and dependency direction.
   - Production adapters, test adapters, mocks, fixtures, and integration seams.
   - Existing tests and failure modes.
3. Name the current ownership boundaries and where they are unclear.
4. Identify coupling, duplicated concepts, hidden dependencies, and abstraction leaks.
5. State what should not change, especially stable public behavior and unrelated modules.
6. Recommend the smallest boundary change that would make the next implementation safer.

## Output Structure

Use concise sections:

```markdown
## Scope

<What code or behavior is being reviewed.>

## Current Shape

<How the subsystem is organized today, with concrete file references.>

## Public Interfaces

- <Exports, routes, commands, events, schemas, or UI contracts.>

## Data Flow

<How data enters, changes, and leaves the subsystem.>

## Call Graph

<Important callers, callees, and dependency direction.>

## Boundary Problems

- <Coupling, duplicated ownership, leakage, unclear responsibility, or test fragility.>

## What Should Not Change

- <Stable behavior, public APIs, unrelated files, or compatibility constraints.>

## Recommended Direction

<The preferred boundary or design adjustment, scoped to the task.>

## Risks

- <Migration, test, performance, security, rollout, or compatibility risk.>

## Validation Plan

- <Checks that would prove the boundary change is safe.>
```

## Decision Rules

- Ground every architectural claim in observed files, symbols, tests, or runtime behavior.
- Prefer boundary clarity over clever abstraction.
- Treat "cleaner" as easier ownership, fewer hidden dependencies, and simpler tests.
- Avoid proposing broad rewrites unless the current structure makes a small correct change unsafe.
- Distinguish current design facts from recommended future design.
- If you cannot inspect the relevant code, give a conditional review and say what evidence is missing.
- Do not make code edits unless the user explicitly asks to implement the recommendation.

## Validation

Before finishing:

- Cite concrete files, functions, classes, routes, or tests where available.
- Confirm the recommendation preserves important public behavior.
- Include at least one test or inspection step that would validate the proposed boundary.
- Name any parts of the system you did not inspect but that could change the conclusion.
