# Personal Agent Skills

This repository stores my personal agent skills. Skills are organized by category in this repo, but each installed skill should live as its own direct child directory in the target agent's skills folder.

## Repository Structure

```text
skills/
├── README.md
├── skills/
|   ├── coding/
|   |   ├── fix-ci-failure/
|   |   ├── review-implementation-options/
|   |   └── write-handoff-prompt/
|   ├── research/
|   |   ├── self-contained-topic-explainer/
|   └── writing/
|       └── collaborative-document-writing/
└── templates/
    └── SKILL.template.md
```

Each skill directory contains a required `SKILL.md` file and may also contain optional `scripts/`, `references/`, or `assets/` directories.

### Coding

> Development workflow helpers, review, CI repair, and agent handoff.

| Skill | Purpose |
| ----- | ------- |
| [`fix-ci-failure`](skills/coding/fix-ci-failure/SKILL.md) | Diagnose CI failures, inspect remote logs, reproduce locally, and make focused fixes |
| [`review-implementation-options`](skills/coding/review-implementation-options/SKILL.md) | Compare minimum-change, clean-refactor, best-practice, and alternative implementation options |
| [`write-handoff-prompt`](skills/coding/write-handoff-prompt/SKILL.md) | Create a durable handoff file and short prompt for another coding agent to continue work |

### Research

> Plain-language explanation, topic grounding, and self-contained learning materials.

| Skill | Purpose |
| ----- | ------- |
| [`self-contained-topic-explainer`](skills/research/self-contained-topic-explainer/SKILL.md) | Write complete explainers for unfamiliar topics or source material so readers do not need to search elsewhere |

### Writing

> Collaborative drafting, revision, and document finalization.

| Skill | Purpose |
| ----- | ------- |
| [`collaborative-document-writing`](skills/writing/collaborative-document-writing/SKILL.md) | Coauthor documents through discovery, outline, drafting, revision, and final review |

## Agent Integration

Skills are installed through flat symlinks directly under each agent's `skills/` directory. Each agent should see skills exactly one level deep:

```text
<agent-skills-dir>/
└── <skill-name> -> <repo>/skills/<domain>/<skill-name>
```

Do not symlink the entire `skills/` directory. Agents will not discover nested domain directories reliably.

Common targets:

- Codex: `$CODEX_HOME/skills`, or `~/.codex/skills` when `CODEX_HOME` is unset.
- Claude Code: `~/.claude/skills` for personal skills, or `.claude/skills` for project-local skills.

## Adding A New Skill

1. Create a new directory under `skills/<domain>/<skill-name>/`.
2. Copy `templates/SKILL.template.md` into that directory as `SKILL.md`.
3. Fill in the frontmatter and keep the body concise.
4. Add optional `references/`, `scripts/`, or `assets/` only when they materially improve reuse.
5. Add an entry to the corresponding domain table in this README.
6. Create flat symlinks in the target agent skills directories:

```bash
ln -sf <repo>/skills/<domain>/<skill-name> ~/.codex/skills/<skill-name>
ln -sf <repo>/skills/<domain>/<skill-name> ~/.claude/skills/<skill-name>
```
