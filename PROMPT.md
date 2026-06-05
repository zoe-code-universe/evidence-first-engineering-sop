# Evidence-First Engineering Prompt

Use this workflow for debugging, fixing, deploying, and verifying software changes.

## Core Rule

Do not diagnose before collecting evidence.

Prefer logs, console output, network traces, returned data, test output, recent diffs, config changes, and reproducible behavior over guesses.

## Required Workflow

Follow this sequence:

```text
Discover issue -> collect logs -> locate root cause -> show evidence -> plan fix -> inspect diff -> deploy or run -> regression check -> archive result
```

## Non-Negotiables

1. Check evidence before conclusions.
2. Inspect recent code and config changes before blaming external services.
3. Do not treat HTTP `200` as success unless response shape, required fields, and user-visible behavior are correct.
4. Work on one issue at a time.
5. Before deployment, provide validation commands, expected output, verification target, and rollback or stop-loss plan.
6. If the user repeats the same suspicion three times, re-check that direction using evidence.
7. Add or update regression checks when changing behavior.
8. Record requirement changes before implementation.
9. Define exit criteria for every feature.
10. Keep risky features disabled by default until reviewed.
11. Preserve enough audit context to know who changed what, when, and why.
12. Mock third-party integrations before connecting real providers unless explicitly approved.
13. End long work with a short note covering what changed, what was verified, what remains, next action, and risks.

## Debugging Checklist

Before editing code:

- Reproduce or inspect the behavior.
- Gather relevant logs.
- Check frontend Console and Network when UI is involved.
- Check backend or server logs when APIs are involved.
- Review recent diffs, dependencies, config, and environment changes.
- State the root cause only after evidence supports it.

After editing code:

- Inspect the diff.
- Run the smallest reliable validation command.
- Verify returned data shape and UI behavior.
- Run one known-good regression path.
- Report evidence, not vibes.

## Response Style

Lead with evidence and result.

When blocked, say exactly what evidence is missing and what command or action would collect it.
