# Claude Code Capability Catalog

Use this file as Codex's selection catalog when optimizing prompts for Claude Code, Claude CLI, `ultracode`, slash commands, skills, agents, MCP, hooks, verification, or plugin-aware work.

Do not copy this catalog into generated prompts. Mention only the commands, skills, agents, or settings that materially improve the user's ask. The target Claude Code session usually already knows its repo, cwd, config, and active tools; avoid explaining that back to it.

Grounding: local Claude Code `2.1.203`; local `~/.claude` inspection on 2026-07-07; official Claude Code docs for commands, skills, dynamic workflows, and model configuration.

## Selection Rules

- Keep generated prompts sparse. A quiet phrase such as "use available project skills, commands, or subagents if they materially improve the work" is often enough.
- Name a slash command only when it is the intended mechanism, such as `/deep-research`, `/code-review ultra`, `/run`, `/verify`, `/batch`, or `ultracode`.
- Prefer capability roles and outcomes over setup lectures. Do not tell the target session what model it is, where it is, or which repo/config it already has.
- Preserve low boundaries: add boundary language only when the user asked for it or the task directly implies risk, destructive changes, factual uncertainty, or scope control.
- For active-chat prompts, assume conversation, files, tool outputs, decisions, and visible session state are already injected.

## Built-In Command Surfaces

| Capability | Use When Helpful |
| --- | --- |
| `/model`, `/effort` | The user explicitly asks to change model/effort or asks for `ultracode`. `ultracode` combines `xhigh` effort with automatic workflow orchestration for substantive tasks. |
| `/plan` | The user wants a planning phase before edits or a large change needs design approval. |
| `/permissions`, `/allowed-tools` | Tool prompts, allowlists, or long runs need permission tuning. |
| `/mcp`, `--mcp-config`, `--strict-mcp-config` | A task depends on MCP servers, reconnecting a server, or restricting servers for a run. |
| `/config`, `/status`, `/settings` | Session settings, workflow toggles, model defaults, theme, output style, or status need adjustment. |
| `/compact`, `/context`, `/clear` | The conversation is context-heavy, stale, or needs a fresh context boundary. |
| `/resume`, `/continue`, `/branch`, `/rewind` | The task should resume, fork, or roll back a conversation/checkpoint. |
| `/fork`, `/background`, `/tasks`, `/goal`, `claude agents` | Work should run in background, continue across turns, or delegate a side lane. |
| `/loop` | A prompt should repeat until a condition changes, such as deployment completion or periodic monitoring. |
| `/diff` | The target needs to inspect current uncommitted changes. |
| `/code-review` | Review current diff or target for correctness bugs and cleanups; `ultra` runs deeper cloud review when appropriate. |
| `/simplify` | Cleanup-only review for reuse, simplification, efficiency, and abstraction fit. |
| `/security-review` | Pending changes need security risk review. |
| `/review` | GitHub PR review, especially when a PR number or open PR is involved. |
| `/run`, `/verify`, `/run-skill-generator` | The task should prove behavior through a running app, or teach Claude Code how to build/launch the app. |
| `/deep-research` | Fan out web/source research, cross-check claims, and return cited synthesis. |
| `/batch` | Large codebase changes that can split into independent worktree units. |
| `/skills`, `/reload-skills` | List, filter, or reload local skills after skill changes. |
| `/plugin`, `/reload-plugins` | Manage or refresh Claude Code plugins. |
| `/doctor`, `/debug` | Diagnose Claude Code install/runtime issues or capture debug logs. |
| `/hooks` | Inspect hook configuration or lifecycle automation. |
| `/memory`, `/init` | Create or refine project `CLAUDE.md` and memory guidance. |
| `/add-dir`, `/cd` | Grant extra directory access or move the session cwd. |
| `/claude-api` | Load API reference, migrate Anthropic SDK code, or create Managed Agent guidance. |
| `/dataviz` | Charts, dashboards, palette/accessibility, and data visualization guidance. |
| `/design-sync`, `/design-login` | Sync a React design system to Claude Design when available and relevant. |
| `/chrome`, `/ide`, `/desktop`, `/remote-control`, `/teleport` | Browser, IDE, desktop, remote, or web-session handoff workflows. |
| `/schedule` | Create or manage scheduled cloud routines. |

## Related CLI Flags

| Flag | Use When Helpful |
| --- | --- |
| `--model`, `--effort` | Launch a session with a chosen model alias or reasoning effort. |
| `--permission-mode`, `--allowedTools`, `--disallowedTools`, `--tools` | Constrain or loosen tool use for a run. |
| `--add-dir`, `--worktree`, `--tmux` | Add file access or isolate work in a git worktree/session. |
| `--agent`, `--agents` | Use or define custom agents for a session. |
| `--plugin-dir`, `--plugin-url` | Load session-specific plugins. |
| `--mcp-config`, `--strict-mcp-config` | Supply or restrict MCP server config. |
| `--continue`, `--resume`, `--fork-session`, `--session-id` | Resume or fork saved sessions. |
| `--print`, `--output-format`, `--input-format`, `--json-schema` | Non-interactive, scripted, streaming, or structured-output runs. |
| `--debug`, `--debug-file`, `--verbose` | Capture logs for troubleshooting. |
| `--chrome`, `--no-chrome`, `--ide`, `--remote-control` | Integrations with Chrome, IDEs, and remote control. |
| `--bare`, `--safe-mode` | Minimal or troubleshooting sessions with customizations disabled. |

## Local Claude Skills Found

| Skill | Use When Helpful |
| --- | --- |
| `browse` | Browserbase/local browser automation, page inspection, screenshots, DOM/network reads, web fetch/search, and Browse.sh skill discovery. |
| `codebase-memory` | Structural code discovery through the knowledge graph: architecture, call paths, symbol lookup, impact analysis, dead code, and repo maps. |
| `find-skills` | Search, vet, and install missing skills from the skills ecosystem. |
| `framer` | Design, edit, publish, or manage Framer websites, CMS, styles, assets, localization, and canvas work. |
| `framer-code-components` | Framer code component constraints and implementation guidance after a Framer project session is established. |
| `framer-project-y27qUUQ1NHmAGGiF6CZB` | Existing project-scoped Framer guidance; use only when that project is the target. |
| `remotion-best-practices` | React/Remotion video creation, animation timing, media components, and render-safe patterns. |
| `resume-tailoring` | Resume or job-application tailoring work. |

## Installed Plugin Skills

`superpowers@claude-plugins-official` is installed and enabled locally. Its skills are useful as workflow posture, not as prompt decoration:

| Skill Area | Use When Helpful |
| --- | --- |
| Brainstorming | Rough idea needs intent refinement before implementation. |
| Writing plans | Approved design needs an executable plan. |
| Git worktrees | Implementation should be isolated from the main working tree. |
| Test-driven development | Code changes need RED/GREEN/REFACTOR discipline. |
| Subagent-driven development | Large implementation can split into task-scoped agents with review. |
| Dispatching parallel agents | Independent research or implementation lanes can run in parallel. |
| Systematic debugging | A bug needs reproduction, hypothesis testing, and root-cause tracing. |
| Requesting/receiving code review | Fresh-context review is needed before completion. |
| Verification before completion | Claims of completion need fresh proof. |
| Finishing a development branch | Completed branch needs final verification and merge/PR/discard options. |
| Writing skills | Creating or improving skills. |

## Local MCP, Hooks, And Config Facts

- `codebase-memory-mcp` is configured in `~/.claude/.mcp.json`; use it for structural code intelligence when available.
- Local hooks include codebase-memory discovery reminders/gates. Do not mention hooks in generated prompts unless hook behavior is relevant.
- Local settings show workflows enabled, default effort `xhigh`, and Superpowers enabled.
- `bypassPermissions` may be configured locally, but generated prompts should not rely on a permission mode unless the user asks for execution conditions.
- Installed plugin list is dynamic; use `/plugin list` or `claude plugin list --available` for fresh discovery when the user asks for missing capabilities.
