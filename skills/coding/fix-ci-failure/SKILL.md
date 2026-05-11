---
name: fix-ci-failure
description: Diagnose and fix failing CI checks for the current Git repository. Use when the user asks to fix CI, investigate a failed PR or commit build, resolve failing tests, repair a broken pipeline, inspect remote CI logs, or make local changes so tests, lint, or build pass again.
---

# Fix CI Failure

Use this skill to repair CI failures with evidence. First identify the failing job and error from CI logs, then reproduce locally when possible, make the smallest relevant fix, and verify with the failing command.

## Trigger Examples

Use this skill when the user asks:

- "Fix the CI failure."
- "The PR checks are failing; help me repair them."
- "Build failed after my commit."
- "Tests are failing in CI."
- "Check the GitHub Actions logs and fix it."
- "The pipeline is red; make it pass."
- "CI 失败了, 帮我修一下"
- "检查一下 CI 日志，帮我修复"


Do not use this skill for:

- Local test failures with no CI or remote context unless the user frames them as CI-related.
- Release engineering changes unrelated to a failing check.
- Infrastructure outages, missing secrets, or permission failures that cannot be fixed in code.

## Workflow

1. Inspect repository state:
   - Confirm the current directory is inside a Git repository.
   - Run `git status --short`.
   - Run `git branch --show-current`.
   - Run `git remote -v`.
   - Note uncommitted user changes and avoid overwriting them.
2. Fetch remote state:
   - Run `git fetch --all --prune`.
   - Do not reset, rebase, force-push, or change remotes unless the user explicitly asks.
3. Identify the CI provider and failing run:
   - For GitHub remotes, prefer `gh pr status`, `gh pr view`, `gh run list`, `gh run view`, and `gh run view --log` when available.
   - If a PR number, run URL, or commit SHA is available from the user, use it directly.
   - If tooling or permission is missing, ask the user for the CI URL or log excerpt.
4. Extract the real failure:
   - Name the failed workflow, job, step, command, and key error lines.
   - Separate primary failure from downstream noise.
   - Check whether the failure is code, test expectation, dependency, environment, secret, quota, or CI configuration.
5. Reproduce locally when possible:
   - Run the same command shown in CI, or the closest local equivalent.
   - If exact reproduction is impossible, explain why and run the most relevant narrower check.
6. Fix the issue:
   - Make the smallest code, test, config, or dependency change that addresses the identified failure.
   - Follow existing project conventions.
   - Do not make unrelated refactors while repairing CI.
7. Verify:
   - Re-run the failed command.
   - Run adjacent checks when the fix touches shared code or config.
   - If CI failed for multiple jobs, verify each distinct failure mode.
8. Report:
   - State the root cause, changed files, commands run, results, and any remaining CI actions such as pushing or rerunning checks.

## Decision Rules

- Evidence first: do not guess the fix before reading the failing job or reproducing locally.
- If CI logs are inaccessible, ask for the missing link or log instead of inventing a failure.
- If the failure is caused by missing secrets, permissions, flaky external services, or infrastructure outage, explain the diagnosis and what the user must change outside code.
- If the CI failure is due to outdated remote state, clarify whether a re-run is enough before changing code.
- If there are user changes in the worktree, inspect before editing and preserve them.
- If a generated file, lockfile, or snapshot is involved, update it only when the project convention requires it.
- If the test is wrong, explain why before changing the test.
- If the code is wrong, add or update a focused test when practical.

## GitHub CLI Commands

Use these when the repository is hosted on GitHub and `gh` is authenticated:

```bash
gh pr status
gh pr view --json number,headRefName,baseRefName,statusCheckRollup,url
gh run list --limit 10
gh run view <run-id> --json name,status,conclusion,jobs
gh run view <run-id> --log
```

Use the command output to locate the failed step and failing command. Do not paste huge logs into the final response; summarize the key lines.

## Validation

Before finishing:

- Re-run the exact failed command, or explain why an exact rerun was not possible.
- Run `git status --short` and confirm only intended files changed.
- Include the verification commands and pass/fail results in the final response.
- If the local checks pass but remote CI still needs a push or manual rerun, say that clearly.

## Final Response

Keep the final response focused:

- Root cause.
- Files changed.
- Verification commands and results.
- Any remaining user action, such as pushing the branch or rerunning CI.
