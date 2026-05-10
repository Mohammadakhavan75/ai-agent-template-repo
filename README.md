# AI-Agent-Ready Project Template

This repository template gives every new project a durable AI-agent operating model.

It is designed for long-lived codebases where an AI agent may develop, debug, refactor, and extend the system over months or years without losing context between sessions.

## Core idea

The AI agent must not rely on conversation memory. It must write durable working context back into the repository.

```text
Repository memory → AI action → tests/checks → repository memory update
```

## What this template provides

- `AGENTS.md` — mandatory operating rules for AI agents.
- `/ai/context/` — stable repo and subsystem memory.
- `/ai/context-packs/` — task-specific context packs.
- `/ai/tasks/` — per-task session logs and plans.
- `/ai/changes/` — AI change records and machine-readable metadata.
- `/docs/invariants/` — subsystem invariants the agent must respect.
- `/docs/adr/` — architectural decision records.
- `/scripts/ai_new_task.sh` — creates a task workspace.
- `/scripts/check_ai_change_policy.py` — CI policy gate.
- GitHub Actions workflow enforcing AI change policy.
- Pull request template enforcing review discipline.

## Quick start

Create a task workspace:

```bash
scripts/ai_new_task.sh TASK-0001 first-feature
```

This creates:

```text
ai/context-packs/TASK-0001-first-feature.md
ai/tasks/TASK-0001-first-feature/session-log.md
ai/tasks/TASK-0001-first-feature/plan.md
```

Then ask your coding agent:

```text
Follow AGENTS.md. Work on TASK-0001-first-feature. Do not edit code until the context pack and plan are prepared.
```

## Expected agent lifecycle

```text
Task intake
  → read AGENTS.md
  → create/update context pack
  → read repo map, subsystem summaries, invariants, ADRs
  → write implementation plan
  → inspect code and tests
  → make minimal change
  → update tests
  → run verification
  → write AI change record
  → update affected summaries
  → run policy check
  → create PR
```

## Local policy check

Before opening a PR:

```bash
python3 scripts/check_ai_change_policy.py
```

By default, the script compares your branch to `origin/main`. You can override this:

```bash
BASE_REF=main python3 scripts/check_ai_change_policy.py
```

## Recommended first customization

Before using this template for a real project, update:

- `ai/context/repo-map.md`
- `ai/context/coding-guidelines.md`
- `ai/context/testing-guidelines.md`
- `docs/invariants/security.md`
- `docs/invariants/concurrency.md`
- `docs/invariants/api-compatibility.md`
- `.github/CODEOWNERS`

## Philosophy

This template assumes:

1. AI agents forget conversation context.
2. Code alone does not explain intent.
3. Long-term maintainability requires provenance.
4. CI should enforce process, not trust prompts.
5. Every meaningful change should be explainable one year later.
