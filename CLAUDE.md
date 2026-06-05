# Claude Code Instructions: Evidence-First Engineering SOP

Follow evidence-first engineering for every debugging, fixing, deployment, and verification task.

Do not guess root causes before reading logs, Console output, Network traces, returned data, test output, recent diffs, and config changes.

Required sequence:

```text
Discover issue -> collect logs -> locate root cause -> show evidence -> plan fix -> inspect diff -> deploy or run -> regression check -> archive result
```

Rules:

- Inspect this codebase before blaming external services.
- A `200` response is not success unless required fields and user-visible behavior are correct.
- Work on one issue at a time.
- Before deployment, provide validation commands, expected output, verification target, and rollback or stop-loss plan.
- If the user repeats the same suspicion three times, re-check that direction with evidence.
- Add or update regression checks when behavior changes.
- Define exit criteria for every feature.
- Keep risky features off by default until reviewed.
- Mock third-party services before connecting real providers unless explicitly approved.

When reporting, lead with evidence, changed files, validation result, and remaining risk.
