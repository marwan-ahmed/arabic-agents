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

To see the difference yourself, read [EXAMPLES.md](EXAMPLES.md): six situations showing the agent with and without the template.

## How to use it

### 1. Pick one version

| | Full `AGENTS.md` | Lite `AGENTS.lite.md` |
| --- | --- | --- |
| Best for | A real project with a database, users, or a team | A small project, a prototype, or your first try of the template |
| Length | ~530 lines (~24 KB) | ~120 lines (~12 KB) |
| Style | Explanations, code examples, and checklists | One line per rule, a short example where needed |
| Left out | — | Token economy (3), code quality (6), session announcements (7.1–7.2), change protocol and migrations (9), quick reference (10), versioning (12) |

Put only one version in your project. Either way the file is saved as `AGENTS.md`, because coding tools look for exactly that name.

### 2. Install the two files

Open a terminal in your project root — the folder with your `package.json`, `pubspec.yaml`, or equivalent — and run **one** command that matches your version and system:

**Full — bash** (macOS / Linux / Git Bash)

```bash
for f in AGENTS.md AGENT_STATE.md; do [ -e "$f" ] && echo "skip $f (exists)" || curl -fsSLo "$f" "https://raw.githubusercontent.com/marwan-ahmed/arabic-agents/main/$f"; done
```

**Full — PowerShell** (Windows)

```powershell
foreach ($f in 'AGENTS.md','AGENT_STATE.md') { if (Test-Path $f) { "skip $f (exists)" } else { Invoke-WebRequest "https://raw.githubusercontent.com/marwan-ahmed/arabic-agents/main/$f" -OutFile $f -UseBasicParsing } }
```

**Lite — bash** (macOS / Linux / Git Bash)

```bash
for s in AGENTS.lite.md AGENT_STATE.md; do f=${s/.lite/}; [ -e "$f" ] && echo "skip $f (exists)" || curl -fsSLo "$f" "https://raw.githubusercontent.com/marwan-ahmed/arabic-agents/main/$s"; done
```

**Lite — PowerShell** (Windows)

```powershell
foreach ($s in 'AGENTS.lite.md','AGENT_STATE.md') { $f = $s -replace '\.lite', ''; if (Test-Path $f) { "skip $f (exists)" } else { Invoke-WebRequest "https://raw.githubusercontent.com/marwan-ahmed/arabic-agents/main/$s" -OutFile $f -UseBasicParsing } }
```

The command downloads two files into your project root: `AGENTS.md` and `AGENT_STATE.md`. If either already exists, it prints `skip … (exists)` and leaves it untouched.

No terminal? Download the two files from this page and put them in your project root. For Lite, rename `AGENTS.lite.md` to `AGENTS.md`.

### 3. Write your project name

Open `AGENTS.md` and, in section 1, replace `<اكتب اسم المشروع هنا>` with your project name:

```yaml
PROJECT_NAME: "my-shop"
```

Leave the other `<auto>` fields as they are; the agent fills them in.

### 4. Start a new session and confirm what the agent shows

Start a new session with your agent and ask for any task. Before writing any code, it should:

1. Read your project files and fill in section 1: languages, frameworks, database, and commands.
2. Show you each value with its source in one message, and ask about anything it could not determine.
3. Wait for your confirmation.

Review the values, correct anything wrong, then confirm. From then on the agent works by the rules in every session.

**If it jumps straight into code,** your tool did not read `AGENTS.md`. It is an [open format](https://agents.md) that many tools read automatically; some need setup.
Tell it in your first message: "Read AGENTS.md in the project root and follow it", and check your tool's documentation so it reads the file every session.

### 5. Add your project's rules (optional)

In section 11 of `AGENTS.md`, write what is specific to your project, one rule per line starting with a dash:

```markdown
- Store every money amount in its smallest unit (integer), never float.
- Never hard-delete an installment contract; archive it.
```

These rules take precedence over the template's rules, except security.

### 6. Before your first commit

- If more than one developer works on the project, add `AGENT_STATE.md` to `.gitignore`, since each developer has their own active module.
- Keep the attribution lines at the end of `AGENTS.md`; the license requires them.

### Check that it works

Give your agent a vague request such as "Add an export button to the customer list". With the template, it should ask about the format, the columns, and who may export before writing any code.
More situations to try are in [EXAMPLES.md](EXAMPLES.md).

### Updating to a newer version

The install command never overwrites an existing file, so:

1. Save your section 11 rules somewhere temporary.
2. Delete `AGENTS.md`, then run the install command again.
3. Put your rules back in section 11 and write the project name. The agent refills the rest of section 1 in the next session.

`AGENT_STATE.md` stays as it is.

## Files

| File | Purpose | Copy into your project? |
| --- | --- | --- |
| [AGENTS.md](AGENTS.md) | The full rules | Yes, or Lite instead |
| [AGENTS.lite.md](AGENTS.lite.md) | The condensed rules | Yes, as `AGENTS.md` |
| [AGENT_STATE.md](AGENT_STATE.md) | Changing work state (current phase, active module) | Yes |
| [EXAMPLES.md](EXAMPLES.md) | Six situations with and without the template | No, for reading |
| [CHANGELOG.md](CHANGELOG.md) | Template version history | No |
| [LICENSE](LICENSE) | License for this template (MIT) | No |
| [NOTICE](NOTICE) | Upstream attribution and license | No |

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

## Version

Current version **2.1.0** — see [CHANGELOG.md](CHANGELOG.md).

## Attribution and license

- Section 2 is adapted from [andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills) by forrestchang (MIT), based on Andrej Karpathy's observations on LLM coding pitfalls. See [NOTICE](NOTICE).
- This template is licensed under [MIT](LICENSE).

**Maintainer:** [Marwan Ahmed](https://marwan-ahmed.com/)
