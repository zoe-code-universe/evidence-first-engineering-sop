---
name: evidence-first-engineering-sop
description: Evidence-first engineering workflow for debugging, fixing, deploying, and verifying software changes. Use when Codex handles technical issues, code changes, deployment tasks, regression checks, production incidents, or GitHub project work, especially when the user expects logs before conclusions, one-task-at-a-time execution, diff review, acceptance criteria, automated validation, and archive notes.
---

# Evidence-First Engineering SOP

## Operating Principle

Treat every technical conclusion as a claim that needs evidence. Prefer logs, console output, network traces, returned data, diffs, and regression results over guesses.

Default to this sequence:

> Discover issue -> collect logs -> locate root cause -> show evidence -> plan fix -> inspect diff -> deploy or run -> zero-cost regression -> archive result

## Non-Negotiables

1. Collect evidence before diagnosis.
   - Check backend logs, frontend Console, browser Network, deployment logs, Nginx or proxy errors, test output, and recent diffs as relevant.
   - Do not explain a root cause when the evidence is incomplete.

2. Inspect own changes before blaming external services.
   - Review recent local edits, commits, environment changes, config changes, and dependency changes first.
   - Only investigate third-party services after internal causes are reasonably excluded.

3. A `200` response is not enough.
   - Verify response shape, required fields, field meanings, UI rendering, and upstream/downstream consistency.
   - Confirm the user-visible workflow works, not merely that the server responds.

4. Work one issue at a time.
   - Keep each task scoped to one clear problem or feature.
   - After a fix, rerun an already-successful workflow to catch regressions.

5. Deployment instructions require acceptance criteria.
   - Include verification commands, expected output, page or API to check, and rollback or stop-loss guidance.
   - Avoid saying only "done" or "deployed."

6. Respect repeated user intuition.
   - If the user raises the same direction three times, re-open that hypothesis and check it against logs and data.

7. Automate validation.
   - Add or update regression tests when changing behavior.
   - Run the smallest reliable validation set before release.

8. Archive requirement changes.
   - Record new ideas, modules, restrictions, or risk decisions before implementation.
   - Include source, purpose, risk, MVP status, and deferred status when applicable.

9. Define exit criteria for every feature.
   - Replace vague tasks such as "make login" with concrete completion rules.
   - Example: authentication is complete when login, logout, error states, refresh persistence, and required audit fields are verified.

10. Keep risk features off by default.
    - Treat public feeds, marketplaces, brand pages, real-name verification, high-risk industries, external domain binding, payments, and deep social sharing as gated features until reviewed.

11. Make user data traceable.
    - For generated content, uploads, phone numbers, submissions, publish status, edits, and takedowns, preserve who/when/what audit context where the system supports it.

12. Mock before integrating real services.
    - Start with mock SMS, real-name verification, payments, content review, WeChat sharing, and external APIs until the core flow is proven.

13. End long work with a daily note.
    - Record what changed, what was verified, what remains, the first next action, and current risks.

## Debugging Workflow

Before changing code:

1. Reproduce or inspect the reported behavior.
2. Gather relevant logs and evidence.
3. Check recent diffs and local code paths.
4. State the smallest credible root cause with evidence.
5. Identify the files and behavior affected.

During the fix:

1. Keep edits focused.
2. Prefer existing project patterns.
3. Inspect the diff before validation or deployment.
4. Avoid unrelated refactors.

After the fix:

1. Run targeted tests or commands.
2. Verify returned data structure and UI behavior.
3. Run at least one known-good path for regression.
4. Record the result and unresolved risk.

## Deployment Workflow

Before deploy:

1. Confirm the exact version or diff being deployed.
2. Provide validation commands and expected outputs.
3. Name the page, endpoint, or workflow to verify.
4. Define what to do if validation fails.

After deploy:

1. Check the live page or endpoint.
2. Inspect logs for new errors.
3. Verify critical data fields and user-visible flow.
4. Update regression coverage or checklist.
5. Archive the deployment note.

## Product Project Defaults

For product projects, apply this SOP automatically to:

- authentication and logout
- onboarding or module selection
- form and questionnaire flows
- generated previews
- sharing links and QR codes
- manual review or approval flows
- public contact display
- publish, unpublish, and takedown behavior

Early-stage integrations should remain mocked unless the user explicitly asks to connect a real provider and the acceptance criteria are clear.
