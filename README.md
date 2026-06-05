# Evidence-First Engineering SOP

**An open workflow that forces AI coding agents to debug like engineers: logs first, conclusions later.**

Most AI coding mistakes do not come from lack of intelligence. They come from weak process:

- guessing before reading logs
- blaming third-party services too early
- treating HTTP `200` as success
- shipping fixes without regression checks
- saying "done" without acceptance criteria

This repository gives AI coding assistants a strict engineering workflow for debugging, fixing, deploying, and verifying software changes.

It works as:

- a Codex skill
- a copy-paste prompt for any AI assistant
- an `AGENTS.md` project instruction file
- a Claude Code instruction file
- a Gemini CLI instruction file
- a Cursor rule
- a GitHub Copilot custom instruction

## Who This Is For

Use this if you work with AI coding agents and want them to be more rigorous, especially for:

- production bugs
- frontend and backend regressions
- deployment checks
- GitHub project maintenance
- agent-built products
- fast-moving MVPs where small mistakes become expensive

It is especially useful when you want AI to behave less like a guesser and more like a careful senior engineer.

## What The Skill Enforces

The core workflow:

```text
Discover issue -> collect logs -> locate root cause -> show evidence -> plan fix -> inspect diff -> deploy or run -> zero-cost regression -> archive result
```

The non-negotiables:

1. Collect logs before diagnosing.
2. Inspect your own code before blaming external services.
3. A `200` response is not enough; verify data structure and UI behavior.
4. Work one issue at a time.
5. Every deployment needs acceptance criteria.
6. Re-check repeated user intuition with evidence.
7. Add or update regression tests.
8. Archive requirement changes.
9. Define exit criteria for each feature.
10. Keep risky features disabled by default.
11. Make user data traceable.
12. Mock third-party services before integrating them.
13. End long work with a clear daily note.

## Use With Any AI

Copy the contents of [`PROMPT.md`](PROMPT.md) into ChatGPT, Claude, Gemini, Copilot Chat, Cursor, or any AI coding assistant before asking it to debug, fix, or deploy code.

Shortest version:

```text
Use evidence-first engineering. Do not diagnose before checking logs, console output, network traces, diffs, returned data, and regression results. Work one issue at a time. After the fix, verify data shape, UI behavior, and a known-good regression path.
```

## Use In AI Coding Tools

Different tools read different instruction files. This repo includes ready-to-copy versions:

| Tool | File |
| --- | --- |
| Any AI chat | [`PROMPT.md`](PROMPT.md) |
| Agentic coding projects | [`AGENTS.md`](AGENTS.md) |
| Codex | [`SKILL.md`](SKILL.md) |
| Claude Code | [`CLAUDE.md`](CLAUDE.md) |
| Gemini CLI | [`GEMINI.md`](GEMINI.md) |
| Cursor | [`.cursor/rules/evidence-first-engineering-sop.mdc`](.cursor/rules/evidence-first-engineering-sop.mdc) |
| GitHub Copilot | [`.github/copilot-instructions.md`](.github/copilot-instructions.md) |

## Install As A Codex Skill

Clone this repository into your Codex skills folder:

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/zoe-code-universe/evidence-first-engineering-sop.git ~/.codex/skills/evidence-first-engineering-sop
```

Restart Codex so the skill can be discovered.

## Use

Invoke it explicitly:

```text
Use $evidence-first-engineering-sop to debug this issue.
```

Or:

```text
Use $evidence-first-engineering-sop to ship this change with logs, diff review, acceptance criteria, regression checks, and archive notes.
```

For other AI assistants, paste [`PROMPT.md`](PROMPT.md) or put the matching instruction file into your project.

## Example Prompts

```text
Use $evidence-first-engineering-sop. The login page returns 200 but the user stays logged out. Find the root cause and fix it.
```

```text
Use $evidence-first-engineering-sop. Before deploying this frontend change, give me the validation commands, expected output, and rollback plan.
```

```text
Use $evidence-first-engineering-sop. The user has reported the same suspicion three times. Re-check that direction using logs before deciding.
```

## Why Star This Repo

Star it if you want a reusable operating system for AI-assisted engineering:

- better debugging discipline
- fewer hallucinated root causes
- clearer deployment standards
- stronger regression habits
- cleaner project archives

This is a small skill, but it encodes a serious rule:

> AI should not be allowed to sound confident before it has evidence.

## 中文说明

这是一个给 AI 编程助手使用的开源工程执行 SOP。

它的目标不是让 AI 写更多代码，而是让 AI 在写代码、修 bug、部署项目时更客观、更严谨。

核心原则：

- 先拿日志，再下结论
- 先查自己，再查别人
- 能跑不等于没问题
- 一次一事，闭环验证
- 部署必须带验收标准
- 用户反复提出的判断，必须重新用日志验证
- 修完必须回归，最后必须归档

如果你也希望 AI 编程助手少猜、多查、稳一点，可以直接复制 `PROMPT.md` 使用，也可以把 `AGENTS.md`、`CLAUDE.md`、`GEMINI.md`、Cursor rules 或 Copilot instructions 放进自己的项目。

## License

MIT
