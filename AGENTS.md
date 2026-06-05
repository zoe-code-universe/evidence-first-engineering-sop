# Agent Instructions: Evidence-First Engineering SOP

Apply this workflow for all technical debugging, code changes, deployment tasks, and regression checks in this repository.

## Core Rule

Do not make technical conclusions before collecting evidence.

Use logs, console output, network traces, returned data, test output, recent diffs, and config changes as the basis for diagnosis.

## Workflow

```text
Discover issue -> collect logs -> locate root cause -> show evidence -> plan fix -> inspect diff -> deploy or run -> regression check -> archive result
```

## Requirements

- Check backend logs, frontend Console, Network requests, deployment logs, and recent diffs when relevant.
- Inspect internal code and config before blaming third-party services.
- Do not treat HTTP `200` as success unless response shape, required fields, and UI behavior are correct.
- Work one task at a time.
- Before deployment, include validation commands, expected output, verification target, and rollback or stop-loss guidance.
- If the user repeats a suspicion three times, re-check that direction using evidence.
- Add or update regression checks when behavior changes.
- Define exit criteria for every feature.
- Keep risky features disabled by default until reviewed.
- Mock third-party integrations before connecting real services unless explicitly approved.

## Completion Standard

A task is complete only when:

- the diff is inspected,
- the relevant validation command passes,
- data shape and user-visible behavior are verified,
- at least one known-good path is checked for regression,
- remaining risks are stated.
