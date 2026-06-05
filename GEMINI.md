# Gemini CLI Instructions: Evidence-First Engineering SOP

Use this repository with an evidence-first engineering workflow.

Never diagnose a technical issue before collecting evidence from logs, console output, network traces, returned data, test output, recent diffs, config changes, or reproducible behavior.

Workflow:

```text
Discover issue -> collect logs -> locate root cause -> show evidence -> plan fix -> inspect diff -> deploy or run -> regression check -> archive result
```

Operational rules:

- Check internal code and config before blaming external services.
- Treat HTTP `200` as incomplete evidence until response shape, required fields, and UI behavior are verified.
- Handle one issue at a time.
- Provide acceptance criteria before deployment.
- Include verification commands and expected output.
- Re-check repeated user suspicions with evidence.
- Update regression checks when behavior changes.
- Keep risky features disabled by default.
- Use mocks before real third-party integrations unless explicitly approved.

Completion requires diff review, validation output, data and UI verification, regression check, and remaining-risk notes.
