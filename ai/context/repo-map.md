# Repository Map

This file is the stable high-level map of the repository.

Update it when major subsystems, ownership boundaries, architectural responsibilities, or build/test conventions change.

## Project purpose

Describe the project in one paragraph.

## Main subsystems

| Subsystem | Responsibility | Main paths | Notes |
|---|---|---|---|
| Core | Primary business/domain logic | `src/` | Replace with actual paths. |
| API | Public/internal interfaces | `api/` | Replace with actual paths. |
| Storage | Persistence, migrations, schemas | `src/storage/`, `migrations/` | Replace with actual paths. |
| Tests | Unit/integration/e2e tests | `tests/` | Replace with actual paths. |
| Docs | Architecture, ADRs, invariants | `docs/` | Stable human/AI memory. |
| AI memory | Context packs, task logs, change records | `ai/` | Required for AI-agent continuity. |

## Critical invariants

- Public API compatibility must be explicitly documented.
- Security-sensitive behavior must fail closed.
- Persistent data changes must include migration and rollback analysis.
- Concurrency-sensitive changes must document race/failure assumptions.

## Build commands

Replace these with real commands:

```bash
# install dependencies
make setup

# run tests
make test

# run lint
make lint

# run all checks
make check
```

## Test strategy

Describe:

- unit test locations;
- integration test locations;
- e2e test locations;
- slow or expensive tests;
- required checks before merge.

## Agent notes

Before changing code, the agent must create/update a task context pack and task plan.
