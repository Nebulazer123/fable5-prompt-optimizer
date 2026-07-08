---
name: fable5-prompt-optimizer
description: Expand rough or ambitious asks into stronger Claude Fable 5 prompts, including active-chat and ultracode/dynamic-workflow prompts, while preserving latitude and avoiding unasked boundaries.
---

# Fable 5 Prompt Optimizer

## Overview

Turn a small user ask into a Fable-5-ready prompt that is more ambitious, clearer about intent, and still open enough for Fable 5 to choose the best method after seeing the real material. When the prompt is for a builder workflow, default to an intelligence handoff that the target builder session can implement.

Read `references/fable5-rules.md` before optimizing. Read `references/capability-contexts.md` when the prompt should draw on a domain-specific capability context such as coding, research, design, animation/UI, vision QA, documents, skill improvement, or `ultracode`. Read `references/claude-code-capabilities.md` when the target surface is Claude Code Desktop, Claude Code CLI, Claude Cowork, `ultracode`, slash commands, skills, agents, MCP, hooks, verification, plugins, or command-aware work. Read `references/examples.md` when the requested prompt shape is unclear, when checking quality, or when the user asks for examples.

## Workflow

1. Identify the moonshot: infer the larger outcome the user is reaching for, not just the literal task words.
2. Detect the run surface: active chat, Claude Code Desktop, Claude Code CLI, Claude Cowork, API/harness, or another builder such as Codex when explicitly relevant.
3. Preserve latitude: keep the method, sequencing, and discovery path open unless the user explicitly asked for a plan, schema, code, or exact steps.
4. Run the Fable preparedness gate: decide whether active chat context is enough, Codex should prepare a context packet first, or Codex should finish/capture one cheap checkpoint before the prompt is sent.
5. Add useful context: include role, purpose, stakes, audience, source material placeholders, and success criteria.
6. Select capabilities quietly: mention Claude Code commands, skills, agents, MCP, hooks, or plugins only when they materially improve the prompt.
7. Remove brittle Fable 5 anti-patterns: no model-name self-introductions in generated prompt bodies, no reasoning echoes, no token countdowns, no unsupported API controls, no aggressive "MUST/CRITICAL" language, and no long procedural micromanagement.
8. Output the optimized prompt first. Add a short rationale or open questions only when they materially help.

## Context Handling

If the optimized prompt will be sent into an already-working chat, assume the existing conversation, attached files, tool outputs, decisions, and constraints will be injected with the prompt. Do not restate or summarize that history. Use a compact context line such as:

```text
Use the conversation, files, tool outputs, and decisions already present in this chat as context. Do not re-derive decisions already made; inspect what is available, then choose the best path.
```

Only use document or source placeholders when the prompt will be pasted into a new chat or external harness that will not have the prior context.

## Fable Preparedness Gate

Use this gate when the prompt will send Fable into a complex active project, review, repo audit, skill improvement, design pass, research synthesis, or any task where Fable would otherwise spend its first turn reconstructing state. The goal is to let Codex do prep before and implementation/verification after, while Fable does the high-intelligence judgment pass with a prepared source packet.

Before producing the final optimized prompt, choose one of three paths:

1. **Active context only**: use the existing chat context when it is compact and complete enough.
2. **Prepared context packet**: have Codex create or point to a Markdown packet when state, evidence, artifacts, or open decisions are spread across files/tools/chat.
3. **Quick checkpoint first**: tell Codex to finish or capture one small nearby thing before packet creation when it materially improves Fable's review.

Use quick checkpoint work sparingly:

- If Codex is close to a natural checkpoint, tell Codex to finish the nearby item first: save the current artifact, run the quick validation already implied by the work, capture the current diff/status, or write down the unresolved decision.
- If there are incomplete tasks that are cheap and necessary for review, tell Codex to complete those before asking Fable for judgment.
- If the missing work is large, risky, destructive, or changes scope, do not stall the prompt. Instead, record the gap in the packet and ask Fable to account for it.

When a packet is useful, create or request a Markdown file with a stable local path. Prefer:

```text
work/fable5-context-packet.md
work/fable5-context/<task-slug>.md
```

In real prompts, include the exact absolute path if Codex created the packet. In examples or reusable docs, use a placeholder or home-relative path instead of a personal absolute path.

When using this skill from Codex and local file/tool access is available, create the packet before returning the final optimized prompt. If packet creation is not possible in the current surface, tell the builder exactly what to capture and use a placeholder path in the prompt.

The packet should be detailed enough that Fable can start with judgment instead of setup:

- User ask and intended run surface.
- Current objective, state, constraints, and decisions already made.
- Target paths, relevant files, repo status/diff, screenshots, links, or artifacts.
- Validation evidence or the reason validation was not run.
- What Codex already tried, changed, tested, or ruled out.
- Known gaps, weak evidence, risks, and open questions.
- The exact judgment, critique, strategy, or handoff Fable should produce.
- What Codex should do after Fable returns the handoff.

When a prepared packet exists, include it in the generated prompt before broader context notes:

```text
Context Packet
Use this prepared context packet as the starting point: `<exact-path>`.
Treat it as a state snapshot. Inspect only what is necessary to make the judgment or handoff stronger.
```

Do not add a packet just to look thorough. Use it when it saves Fable from avoidable state reconstruction, makes review materially more accurate, or gives subagents a shared starting snapshot.

## New Chat And File Path Handling

If the prompt is for a first-time or standalone chat, carry forward the target paths, source names, and context needed to locate the material. Use quiet source-loading language such as:

```text
Use the target path/source material below as the starting point.
```

For local skill-improvement asks, do not tell Fable 5 to load the entire tree automatically. Use progressive loading:

1. Read the target `SKILL.md` first.
2. Inspect the target skill tree.
3. Read the files that `SKILL.md` directly references and any files made relevant by the user's ask.
4. Only read all references/tests/scripts when the ask explicitly calls for a deep audit, maximum improvement pass, or broad public-readiness pass.

When a local path is supplied, include a compact `Target` or `Source Material` section with the path. If no path is supplied and the prompt will run in a standalone context, ask for the path or add a placeholder instead of pretending the prompt can locate the material.

## Implementation Handoff Mode

Default to this mode when the user wants an ambiguous/intelligent upgrade, a "moonshot" pass, or a prompt that will guide later execution in Claude Code Desktop, Claude Code CLI, Claude Cowork, an API/harness, Codex, or another builder. The target prompt's job is the intelligence pass: sharpen the ambition, infer the strongest interpretation, surface assumptions and tradeoffs, sketch the implementation direction, define acceptance criteria, and identify verification signals. The builder session does the execution work: inspect files, edit code, run commands, create artifacts, and verify.

Do not ask Fable 5 to run tools, edit files, or implement the change unless the user explicitly says the target Claude Code, Cowork, API/harness, Codex, or other builder session should execute. Ask for an implementation-ready handoff instead.

Ask for visible rationale, decision points, assumptions, tradeoffs, and implementation shape. Do not ask for hidden chain-of-thought, "all thinking", or "show your reasoning"; rewrite those as "show the useful rationale the builder needs to implement well."

Keep the handoff detailed but efficient. Compress repeated context, avoid long task choreography, and prioritize the details that would change what the builder does next.

## Model-Name Rule

Generated optimized prompt bodies must not introduce or label the target model by name. Do not write role lines that name the model, even when the user says "for Fable 5." Use capability-role language instead, such as "Act as a high-intelligence design pass," "Act as a senior research strategist," or "Act as the architecture and implementation-intelligence pass."

Skill documentation, file names, attribution, and API/model notes may still mention Fable 5 when describing the skill or platform facts.

## Claude Code Capability Selection

When a prompt is meant for Claude Code or Claude CLI, use `references/claude-code-capabilities.md` as Codex's private selection catalog. The generated prompt should not recite that catalog. It should name a command, skill, agent pattern, MCP server, hook, or plugin only when that tool is a real mechanism for the user's requested work.

Prefer quiet capability hints:

```text
Use available project skills, commands, or subagents if they materially improve the work.
```

Do not tell the target session what it is, where it is, which repo it is in, or which config it already knows from the active session. Avoid meta setup language unless the user is explicitly asking for a standalone Claude CLI command, a new session launch, or a config change.

Good selective mentions:

- Use `/deep-research` only for source-fanout research where citations and cross-checking matter.
- Use `/code-review`, `/simplify`, or `/security-review` only for review-oriented diff work.
- Use `/run` or `/verify` only when the prompt should ask Claude Code to prove behavior in a running app.
- Use `/batch` or `ultracode` only for large parallel work where workflow orchestration would help.
- Use local skills such as `codebase-memory`, `browse`, `framer`, or `remotion-best-practices` only when the ask directly matches those capabilities.

## Ultracode And Dynamic Workflows

When the user says `ultracode`, `dynamic workflow`, `use a workflow`, `many subagents`, or describes a codebase-wide audit, large migration, cross-checked research job, long-running build, or multi-angle verification task, preserve the workflow signal. Treat `ultracode` as Claude Code's workflow trigger/setting, not as generic "try harder" wording.

For these prompts, add a short `Workflow Mode` section only when useful:

```text
Workflow Mode
Use ultracode/dynamic workflows when the task is large enough to benefit from scripted orchestration. Fan out independent work to focused subagents, keep the main session responsive, cross-check important findings, and synthesize the strongest result back into one answer.
```

Keep this high-level. Do not script every phase, assign exact agent counts, or force a workflow when a normal pass is enough. If the user wants many spawned agents, ask Fable 5 to choose the decomposition after inspecting the real repo/material and to use fresh-context verifier agents for important claims.

## Output Shape

Default to this prompt-first shape:

```text
Role & Objective
...

Context
...

Ambition
...

What To Explore
...

Output
...

Boundaries
... (only when requested or clearly implied)
```

Use headings as scaffolding, not a rigid template. Omit headings that do not help the prompt.

Use as little boundary verbiage as possible. Do not auto-add boundary instructions the user did not ask for and that are not explicitly implied by the request. Include a `Boundaries` section only when the source ask involves safety, scope control, destructive actions, factual risk, implementation restraint, or another clearly implied constraint.

For Claude Code prompts, add a short `Workflow Mode` section only when the user asks for `ultracode`, workflows, many subagents, agent teams, or a task that obviously needs large-scale parallel verification.

For implementation-handoff prompts, add a short `Handoff` or `Output` instruction that asks for a ready-to-use implementation brief: strongest direction, key decisions, implementation shape, acceptance criteria, verification plan, risks, and any truly blocking open questions.

For prompts that reference local files, include the exact paths and a short context-loading instruction. Do not assume the target can locate source material without a path or placeholder.

For API-target prompts, add a short `Fable 5 API notes` section only when the user asks for API use or mentions SDKs, agents, tools, harnesses, batch, streaming, parameters, or model IDs.

When a prepared context packet exists, include a `Context Packet` section with the exact path before broader context notes.

## Style Rules

- Make the first paragraph broad and high-agency.
- Do not name the target model in generated prompt bodies.
- Prefer phrases like "look for the highest-leverage path" over exact step lists.
- Add dimensions to investigate, not a predetermined answer.
- In active-chat prompts, lean on the existing chat context instead of reprinting it.
- In standalone prompts, include the minimum path/context needed for the target chat to find the material.
- Ask for missing context inside an optional `Open questions` section after the prompt; do not block output unless the ask is empty.
- Keep the final optimized prompt copyable. Do not wrap it in commentary-heavy audit blocks by default.
- If the user asks for only the prompt, return only the prompt.
- If the target is an implementation handoff, make it clear that Fable should produce the design/handoff and the builder session will perform the implementation unless the user explicitly requested execution in the target session.

## Quality Gate

Before responding, verify:

- The output is more ambitious than the input.
- The output keeps room for discovery and judgment.
- The output does not become a rigid implementation plan.
- Generated prompt bodies do not name the target model.
- Active-chat prompts do not duplicate already-injected context.
- Prepared context packets are used only when they reduce reconstruction work, improve review quality, or give subagents a shared state snapshot.
- If Codex is close to a useful checkpoint, the skill tells Codex to finish/capture only the cheap relevant item before sending the prompt.
- Large missing work is recorded as a packet gap instead of blocking prompt creation.
- Standalone prompts include supplied file paths and context needed to locate material.
- File-path prompts use progressive loading instead of forcing full-tree loading.
- Claude Code prompts mention only relevant commands, skills, agents, MCP, hooks, or plugins.
- Implementation-handoff prompts ask for visible rationale and handoff detail without requesting hidden chain-of-thought.
- Implementation-handoff prompts do not make Fable perform builder execution work unless the user asked for execution.
- Ultracode prompts preserve the workflow signal without hard-coding agent choreography.
- The output uses Fable 5 guidance from `references/fable5-rules.md`.
- Any adapted upstream rule language respects the MIT attribution in `references/upstream-license.txt`.
