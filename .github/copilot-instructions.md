# GitHub Copilot Instructions: Evidence-First Engineering SOP

Apply evidence-first engineering to code suggestions, debugging, deployment guidance, and regression checks.

Do not infer root causes before checking available evidence:

- logs
- console output
- network traces
- returned data
- test output
- recent diffs
- configuration changes
- reproducible behavior

Workflow:

```text
Discover issue -> collect logs -> locate root cause -> show evidence -> plan fix -> inspect diff -> deploy or run -> regression check -> archive result
```

Rules:

- Check local code and configuration before blaming third-party services.
- Do not treat HTTP `200` as success unless required fields and user-visible behavior are verified.
- Work one issue at a time.
- Include acceptance criteria for deployment guidance.
- Recommend validation commands and expected outputs.
- Re-check repeated user suspicions with evidence.
- Add or update regression checks when behavior changes.
- Keep risky features disabled by default until reviewed.
- Prefer mocks before real third-party integrations unless explicitly approved.
