<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/logo-dark.svg">
    <source media="(prefers-color-scheme: light)" srcset="assets/logo-light.svg">
    <img alt="Fable 5 Prompt Optimizer" src="assets/logo-light.svg" width="96">
  </picture>

  <h1>Fable 5 Prompt Optimizer</h1>
  <p>Turn rough Codex asks into sharper Claude Fable 5 handoff prompts without over-deciding the build.</p>
</div>

<div align="center">

[![License: MIT][license-shield]][license-url]
[![Skill: Codex][codex-shield]][codex-url]
[![Claude Code][claude-code-shield]][claude-code-url]

</div>

<div align="center">
  <a href="#why">Why</a> &middot;
  <a href="#features">Features</a> &middot;
  <a href="#quick-start">Quick Start</a> &middot;
  <a href="#install">Install</a>
</div>

## Why

Use this when a short, ambitious ask needs to become a strong Fable 5 prompt before Codex implements it. The skill keeps the ask open enough for Fable 5 to make good judgment calls, while still giving Codex a clear handoff to build from.

It is for Codex and Claude Code users who want better prompts for ambiguous work, active-chat context, `ultracode` workflow runs, or moonshot planning passes. It is not a generic prompt expander and it does not try to make Fable 5 edit files unless you explicitly ask for a Claude Code execution prompt.

## Features

- **Codex-ready handoffs** - Frames Fable 5 as the design and decision pass, then leaves implementation, commands, artifacts, and verification to Codex.
- **Ambition without micromanagement** - Expands the stakes, quality bar, and exploration space without turning every ask into a rigid plan.
- **Active-chat aware prompts** - Assumes existing chat history, files, tool outputs, and decisions are already available when the prompt is going into a live session.
- **Ultracode-aware wording** - Preserves Claude Code `ultracode` and dynamic-workflow intent without hard-coding agent counts or a brittle phase script.
- **Fable 5 cleanup rules** - Removes hidden-reasoning requests, token countdowns, unsupported API parameters, and excessive compliance language.
- **Public attribution** - Keeps MIT attribution for upstream material adapted from `CheswickDEV/claude-fable-5-prompt-optimizer`.

## Quick Start

```text
"/fable5-prompt-optimizer make this portfolio plan way more ambitious"
"$fable5-prompt-optimizer upgrade this rough ask before Codex builds"
"optimize this for Fable 5 ultracode with dynamic workflows"
```

Each invocation returns the upgraded prompt first. If useful, it may add a short rationale or a few open questions after the prompt.

## Usage

The skill is designed for prompts like:

```text
make this more moonshot
turn this into a stronger handoff prompt for a coding agent
make this more ambitious but don't tell it exactly how to do it
ultracode this whole chat with many subagents
optimize for Fable 5
```

Sample output shape:

```text
Role & Objective
Act as the high-intelligence design pass before Codex implements...

Context
Use the existing chat, files, tool outputs, and decisions as context...

Ambition
Infer the bigger outcome the user is reaching for...

What To Explore
- The strongest interpretation of the goal
- The implementation shape Codex should consider
- Acceptance criteria and verification signals

Output
Return the Codex-ready handoff first...
```

## Install

### Codex

Clone the repository and link it into your Codex skills directory:

```bash
git clone https://github.com/Nebulazer123/fable5-prompt-optimizer.git ~/skills/fable5-prompt-optimizer
ln -sfn ~/skills/fable5-prompt-optimizer ~/.codex/skills/fable5-prompt-optimizer
```

Restart Codex or start a new chat, then invoke:

```text
/fable5-prompt-optimizer
```

### Claude Code

Claude Code can read agent skills from `~/.claude/skills`:

```bash
git clone https://github.com/Nebulazer123/fable5-prompt-optimizer.git ~/skills/fable5-prompt-optimizer
ln -sfn ~/skills/fable5-prompt-optimizer ~/.claude/skills/fable5-prompt-optimizer
```

Then use the skill name in a prompt:

```text
Use fable5-prompt-optimizer to upgrade this ask for Fable 5 before Codex builds it.
```

## Prerequisites

| Dependency | Purpose | Setup |
|---|---|---|
| [Codex](https://openai.com/codex/) | Primary environment for using the skill as a local Codex skill. | Add the repo to `~/.codex/skills/fable5-prompt-optimizer`. |
| [Claude Code](https://www.anthropic.com/claude-code) | Optional target environment for Claude Code and `ultracode` prompts. | Add the repo to `~/.claude/skills/fable5-prompt-optimizer`. |
| [Git](https://git-scm.com/) | Clones and updates the skill. | macOS: `xcode-select --install` or `brew install git`. |

No API keys, hosted services, or paid accounts are required by the skill itself.

## What's Inside

```text
SKILL.md                         Skill instructions and trigger behavior
agents/openai.yaml               Codex display metadata
references/fable5-rules.md       Fable 5 prompting rules used by the skill
references/examples.md           Before/after examples
references/upstream-license.txt  MIT attribution for adapted upstream material
```

## Development

Validate the skill with Codex's skill validator:

```bash
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py .
```

Check the repository for accidental local paths or secrets before publishing:

```bash
rg -n "Users/|api[_-]?key|token|secret|password" .
```

## Contributing

Contributions are welcome when they keep the skill focused: stronger Fable 5 prompts, less over-prescription, cleaner active-chat behavior, and better Codex handoffs. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT - see [LICENSE](LICENSE). Portions of the prompting rules adapt MIT-licensed material from `CheswickDEV/claude-fable-5-prompt-optimizer`; see [NOTICE.md](NOTICE.md) and [references/upstream-license.txt](references/upstream-license.txt).

[license-shield]: https://img.shields.io/badge/License-MIT-2f6f4e.svg
[license-url]: LICENSE
[codex-shield]: https://img.shields.io/badge/Codex-skill-1f6feb.svg
[codex-url]: #codex
[claude-code-shield]: https://img.shields.io/badge/Claude_Code-compatible-4b5563.svg
[claude-code-url]: #claude-code
