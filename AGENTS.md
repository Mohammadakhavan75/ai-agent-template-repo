# AI Agent Operating Rules

You are working in a long-lived production repository.

Your responsibility is not only to modify code. Your responsibility is to preserve the future understandability, safety, and maintainability of the system.

## Mandatory lifecycle

For every non-trivial task, follow this lifecycle:

1. Read this file: `AGENTS.md`.
2. Read the repository map: `ai/context/repo-map.md`.
3. Create or update a task context pack under `ai/context-packs/`.
4. Create or update a task workspace under `ai/tasks/`.
5. Read relevant subsystem summaries under `ai/context/`.
6. Read relevant invariant documents under `docs/invariants/`.
7. Read relevant ADRs under `docs/adr/`.
8. Identify relevant code and tests before editing.
9. Write or update the task implementation plan before editing code.
10. Make the minimal safe change.
11. Add or update tests, or document why tests are not applicable.
12. Run relevant verification commands.
13. Create or update an AI change record under `ai/changes/`.
14. Update affected context summaries if behavior, architecture, or ownership changed.
15. Run the AI policy check before proposing the change.

## Forbidden behavior

Do not:

- edit code before understanding the relevant context;
- make broad refactors without explicit justification;
- modify public APIs without compatibility analysis;
- modify security-sensitive code without reading security invariants;
- modify concurrency-sensitive code without reading concurrency invariants;
- claim tests passed unless the commands were actually run;
- hide uncertainty;
- delete existing behavior without documenting the compatibility impact;
- leave unresolved TODOs without tracking them in the task log;
- create undocumented behavior changes.

## Required artifacts for behavioral changes

A behavioral change must include:

- task context pack;
- task plan;
- test update or explicit test justification;
- AI change record in Markdown;
- AI change metadata in YAML;
- rollback plan;
- risk section.

## Required artifacts for architectural changes

An architectural change must include:

- ADR;
- updated architecture/context summary;
- migration or compatibility note;
- affected invariant review;
- rollback or mitigation plan.

## Session resume protocol

When resuming a task:

1. Read the task context pack.
2. Read the task session log.
3. Read the task plan.
4. Read related AI change records.
5. Summarize the current objective, known state, blockers, and next step.
6. Continue from the recorded next step.

At the end of every work session, update:

- files inspected;
- findings;
- commands run;
- test results;
- open questions;
- next step.

## Retrieval-before-editing rule

Before editing a file, identify:

1. its responsibility;
2. direct callers/callees when relevant;
3. relevant tests;
4. related invariants;
5. related ADRs or previous change records.

Do not edit a file if its role in the system is unknown.

## PR expectations

Every PR should explain:

- problem;
- solution;
- context pack;
- AI change record;
- files changed;
- tests run;
- risks;
- rollback plan;
- open questions.
