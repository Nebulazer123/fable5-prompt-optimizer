# Claude Code Capability Catalog

Use this file as Codex's selection catalog when optimizing prompts for Claude Code, Claude CLI, `ultracode`, slash commands, skills, agents, MCP, hooks, verification, or plugin-aware work.

Do not copy this catalog into generated prompts. Mention only the commands, skills, agents, or settings that materially improve the user's ask. The target Claude Code session usually already knows its repo, cwd, config, and active tools; avoid explaining that back to it.

Grounding: local Claude Code `2.1.203`; local `~/.claude` inspection on 2026-07-07; local slash-command inventory generated on 2026-07-07; official Claude Code docs for commands, skills, dynamic workflows, and model configuration.

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

## Local Inventory-Backed Slash Commands

These commands were found in the local slash-command inventory generated on 2026-07-07. Use them as a pick-list for Claude Code Desktop, Claude Code CLI, Claude Cowork, and plugin-aware handoff prompts. Generated prompts should name only the relevant command, not this whole inventory.

| Command | Surface | Use When Helpful |
| --- | --- | --- |
| `/bootstrap` | vercel | Bootstrap a repository with Vercel-linked resources by running preflight checks, provisioning integrations, verifying env keys, and then executing db/dev startup commands safely. |
| `/build-agent` | cloudflare | Build an AI agent on Cloudflare using the Agents SDK. |
| `/build-and-run-macos-app` | build-macos-apps | Create or update the project-local macOS `build_and_run.sh` script, wire the Codex app Run button, then use that script as the default build/run entrypoint. |
| `/build-mcp` | cloudflare | Build a remote MCP server on Cloudflare with tools and OAuth. |
| `/build-zoom-apps-sdk-app` | zoom | Implement a Zoom Apps SDK app that runs inside the Zoom client with the right running context, auth path, and backend integration. |
| `/build-zoom-bot` | zoom | Implement a Zoom meeting bot, recorder, or real-time media workflow in the current codebase. |
| `/build-zoom-cobrowse-app` | zoom | Implement a Zoom Cobrowse integration with session lifecycle, privacy controls, and support workflow wiring. |
| `/build-zoom-contact-center-app` | zoom | Implement a Zoom Contact Center integration for web, mobile, or backend workflows with the right auth and event handling. |
| `/build-zoom-meeting-app` | zoom | Implement an embedded or managed Zoom meeting flow in the current codebase with the right SDK and auth path. |
| `/build-zoom-meeting-sdk-app` | zoom | Implement a Zoom Meeting SDK integration with the right platform-specific join or start flow, auth path, and verification loop. |
| `/build-zoom-phone-integration` | zoom | Implement a Zoom Phone integration around APIs, Smart Embed, calling flows, and event handling. |
| `/build-zoom-probe-flow` | zoom | Implement readiness checks with Zoom Probe SDK before users join meetings or sessions. |
| `/build-zoom-rest-api-app` | zoom | Implement a Zoom REST API integration with the right resources, auth path, and verification loop. |
| `/build-zoom-rivet-app` | zoom | Implement a server-side Zoom integration with Rivet modules for auth, APIs, webhooks, and deployment-safe composition. |
| `/build-zoom-rtms-app` | zoom | Implement a Zoom RTMS workflow for live media, transcript, or event-stream processing with the right stream lifecycle and backend handling. |
| `/build-zoom-scribe-app` | zoom | Implement a Zoom Scribe transcription pipeline for uploaded or stored media with the right processing mode and callback flow. |
| `/build-zoom-team-chat-app` | zoom | Implement a Zoom Team Chat integration or chatbot flow with the right auth, eventing, and message handling. |
| `/build-zoom-ui-toolkit-app` | zoom | Implement a Zoom Video SDK UI Toolkit integration for a prebuilt web session UI with the right auth, mount strategy, and session lifecycle. |
| `/build-zoom-video-sdk-app` | zoom | Implement a custom Zoom Video SDK session workflow with the right auth, session lifecycle, and verification path. |
| `/build-zoom-virtual-agent` | zoom | Implement a Zoom Virtual Agent integration for web or mobile wrapper environments with the right lifecycle and event handling. |
| `/cancel-ralph` | ralph-loop | Cancel active Ralph Loop work. |
| `/clean_gone` | commit-commands | Clean up git branches marked as gone, including associated worktrees. |
| `/code-review` | code-review | Review a pull request or code changes through the installed code-review command. |
| `/commit` | commit-commands | Create a git commit. |
| `/commit-push-pr` | commit-commands | Commit, push, and open a PR. |
| `/compact` | built-in | Compact a context-heavy session. |
| `/config` | built-in | Inspect or change settings/session control. |
| `/configure` | hookify | Enable or disable Hookify rules interactively. |
| `/connect-figma-components` | figma | Create or update parserless Figma Code Connect template files for components. |
| `/context` | built-in/custom | Inspect or manage context when the local app exposes it. |
| `/create-design-system-rules` | figma | Generate project-specific Figma-to-code rules and prepare them for project instructions. |
| `/create-docker-mcp-tunnel` | mcp-tunnels | Stand up an Anthropic MCP tunnel locally with Docker Compose for a private MCP server. |
| `/create-plugin` | plugin-dev | Run a guided end-to-end plugin creation workflow. |
| `/debug-zoom` | zoom | Triage a broken Zoom integration when the failing layer is unclear. |
| `/debug-zoom-auth` | zoom | Isolate and fix Zoom authentication failures across OAuth, SDK signatures, and token refresh paths. |
| `/debug-zoom-webhook` | zoom | Diagnose Zoom webhook issues across validation, signatures, delivery, retries, and handlers. |
| `/deploy` | vercel | Deploy the current project to Vercel, preview by default or production when requested. |
| `/env` | vercel | List, pull, add, remove, or diff Vercel environment variables. |
| `/example-command` | example-plugin | Reference command-frontmatter behavior when developing or testing plugin commands. |
| `/feature-dev` | feature-dev | Run guided feature development with codebase understanding and architecture focus. |
| `/fix-codesign-error` | build-macos-apps | Inspect a macOS signing or entitlement failure and identify the minimum fix path. |
| `/help` | hookify/ralph-loop | Get plugin help when the active plugin is Hookify or Ralph Loop. |
| `/hookify` | hookify | Create hooks to prevent unwanted behaviors from conversation analysis or explicit instructions. |
| `/implement-from-figma` | figma | Implement a Figma frame or component into project code. |
| `/init` | built-in | Initialize app/CLI project guidance. |
| `/list` | hookify | List configured Hookify rules. |
| `/maker-setup` | cwc-makers | Onboard a Code-with-Claude Makers Cardputer and install the Claude Buddy app bundle. |
| `/marketplace` | vercel | Discover and install Vercel Marketplace integrations. |
| `/model` | built-in | Use the local model/session picker. |
| `/modernize-assess` | code-modernization | Inventory and size a legacy system by complexity, debt, and relative scale. |
| `/modernize-brief` | code-modernization | Generate the phased Modernization Brief that transformation agents will execute against. |
| `/modernize-extract-rules` | code-modernization | Mine business logic from legacy code into testable, human-readable rule specs. |
| `/modernize-harden` | code-modernization | Run a security vulnerability scan with reviewable remediation patches. |
| `/modernize-map` | code-modernization | Map dependencies, topology, call graphs, data lineage, and batch flows. |
| `/modernize-preflight` | code-modernization | Check modernization readiness: tools, build chain, source completeness, and telemetry access. |
| `/modernize-reimagine` | code-modernization | Coordinate a multi-agent greenfield rebuild from extracted legacy specs. |
| `/modernize-status` | code-modernization | Report modernization artifact inventory, staleness, secrets hygiene, and next step. |
| `/modernize-transform` | code-modernization | Transform one legacy module to the target stack with behavior-equivalence tests. |
| `/modernize-uplift` | code-modernization | Same-stack version uplift while preserving behavior and proving equivalence. |
| `/new-sdk-app` | agent-sdk-dev | Create and set up a new Claude Agent SDK application. |
| `/plan-zoom-integration` | zoom | Turn a Zoom product idea into a practical build plan with auth, architecture, milestones, and risk calls. |
| `/plan-zoom-product` | zoom | Choose the right Zoom product surface for a use case and explain tradeoffs. |
| `/ralph-loop` | ralph-loop | Start Ralph Loop in the current session. |
| `/review-design-parity` | figma | Review implemented UI against a Figma design and call out visual or behavioral mismatches. |
| `/review-pr` | pr-review-toolkit | Run comprehensive PR review using specialized agents. |
| `/revise-claude-md` | claude-md-management | Update `CLAUDE.md` with useful learnings from the current session. |
| `/schedule` | built-in | Create or manage scheduled automation routines. |
| `/setup-codex-run-actions` | expo | Wire the current Expo project into the Codex app action bar. |
| `/setup-zoom-oauth` | zoom | Inspect the repository and set up the right Zoom OAuth path, scopes, redirects, and token lifecycle. |
| `/setup-zoom-webhooks` | zoom | Implement or correct a Zoom webhook receiver with endpoint validation, signatures, and reliable delivery. |
| `/setup-zoom-websockets` | zoom | Implement or correct a Zoom WebSocket event stream with lifecycle, auth, and reconnect handling. |
| `/status` | vercel | Show Vercel project status, recent deployments, linked project info, and environment overview. |
| `/test-macos-app` | build-macos-apps | Run the smallest meaningful macOS test scope first and explain failures by category. |
| `/usage` | built-in | Inspect usage/account information. |
| `/workflows` | built-in | Inspect or manage app workflow UI where available. |
| `/zoom-integration-doctor` | zoom | Run a read-first audit of Zoom architecture, auth, eventing, and SDK risks. |

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
