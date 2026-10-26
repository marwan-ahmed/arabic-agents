# Arabic AGENTS.md Template

**A working contract for AI coding agents: less code, stronger security, and questions before mistakes — not after.**

By [Marwan Ahmed](https://marwan-ahmed.com/) · [العربية](README.md)

One rules file you drop into your project root; your coding agent reads it at the start of every session.
You write only the project name. The agent infers the rest (languages, frameworks, database, commands)
from the project's own files and shows it to you for confirmation.

> The template itself is written in Arabic, keeping technical terms in English as developers use them.

## Why this template?

- **Stops over-engineering:** Karpathy's four principles — think before coding, simplicity first, surgical changes, goal-driven execution.
- **Security is a requirement, not an option:** authentication and authorization, multi-tenancy isolation, input validation, secrets, and forbidden patterns.
- **Governs the agent's own actions:** external content is data, not instructions; approval before destructive commands; no commits unless asked; verify packages before installing.
- **Arabic-first:** a ready rule set for Arabic-speaking teams.

## Files

| File | Purpose |
| --- | --- |
| [AGENTS.md](AGENTS.md) | The rules — copy into your project |
| [AGENTS.lite.md](AGENTS.lite.md) | A condensed version of the rules — copy into your project as `AGENTS.md` instead of the full one |
| [AGENT_STATE.md](AGENT_STATE.md) | Changing work state (current phase, active module) — copy into your project |
| [CHANGELOG.md](CHANGELOG.md) | Template version history |
| [LICENSE](LICENSE) | License for this template (MIT) |
| [NOTICE](NOTICE) | Upstream attribution and license |

## What's inside

| Section | Topic |
| --- | --- |
| 0 | Core principles and conflict priority |
| 1 | Project identity and initialization protocol |
| 2 | Way of working (Karpathy's four principles) |
| 3 | Token economy |
| 4 | Hallucination prevention |
| 5 | Security, including agent operating rules (5.7) |
| 6 | Code quality |
| 7 | Context management |
| 8 | Forbidden patterns |
| 9 | Change protocol and migrations |
| 10 | Quick reference |
| 11 | Your project-specific rules |
| 12 | Versioning and maintenance |

## Lite version

`AGENTS.lite.md` keeps the core rules in condensed form, without repetition, so each session loads less context. Its section numbers match the full version.

| | Full `AGENTS.md` | Lite `AGENTS.lite.md` |
| --- | --- | --- |
| Length | ~530 lines (~24 KB) | ~120 lines (~12 KB) |
| Sections | 0–12 | 0, 1, 2, 4, 5, 7.3–7.4, 8, 11 |
| Style | Explanations, code examples, and checklists | One line per rule, a short example where needed |
| Left out | — | Token economy (3), code quality (6), session announcements (7.1–7.2), change protocol and migrations (9), quick reference (10), versioning (12) |

## Install

Run one of these from your project root. It downloads both files and never overwrites an existing one.

**bash** — macOS / Linux / Git Bash

```bash
for f in AGENTS.md AGENT_STATE.md; do [ -e "$f" ] && echo "skip $f (exists)" || curl -fsSLo "$f" "https://raw.githubusercontent.com/marwan-ahmed/arabic-agents/main/$f"; done
```

**PowerShell** — Windows

```powershell
foreach ($f in 'AGENTS.md','AGENT_STATE.md') { if (Test-Path $f) { "skip $f (exists)" } else { Invoke-WebRequest "https://raw.githubusercontent.com/marwan-ahmed/arabic-agents/main/$f" -OutFile $f -UseBasicParsing } }
```

**Or the Lite version:** these save `AGENTS.lite.md` as `AGENTS.md`, along with `AGENT_STATE.md`, and never overwrite an existing file.

**bash** — macOS / Linux / Git Bash

```bash
for s in AGENTS.lite.md AGENT_STATE.md; do f=${s/.lite/}; [ -e "$f" ] && echo "skip $f (exists)" || curl -fsSLo "$f" "https://raw.githubusercontent.com/marwan-ahmed/arabic-agents/main/$s"; done
```

**PowerShell** — Windows

```powershell
foreach ($s in 'AGENTS.lite.md','AGENT_STATE.md') { $f = $s -replace '\.lite', ''; if (Test-Path $f) { "skip $f (exists)" } else { Invoke-WebRequest "https://raw.githubusercontent.com/marwan-ahmed/arabic-agents/main/$s" -OutFile $f -UseBasicParsing } }
```

## Usage

1. Add `AGENTS.md` and `AGENT_STATE.md` to your project root with the install command above, or copy them manually.
2. Set `PROJECT_NAME` in section 1.
3. Start a session with your agent: it infers the remaining fields from the project files (section 1.1), shows each value with its source, and waits for your confirmation.
4. Add your project's rules in section 11.
5. In teams: add `AGENT_STATE.md` to `.gitignore`, since each developer has their own active module.
6. Keep the attribution line at the end of `AGENTS.md`; the upstream license requires it.

## Compatibility

`AGENTS.md` is an [open format](https://agents.md) read by many AI coding tools.
If your tool reads a different filename, check its documentation for how to point it to `AGENTS.md`.

## Version

Current version **2.1.0** — see [CHANGELOG.md](CHANGELOG.md).

## Attribution and license

- Section 2 is adapted from [andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills) by forrestchang (MIT), based on Andrej Karpathy's observations on LLM coding pitfalls. See [NOTICE](NOTICE).
- This template is licensed under [MIT](LICENSE).

**Maintainer:** [Marwan Ahmed](https://marwan-ahmed.com/)
