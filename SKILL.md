---
name: fable5-prompt-optimizer
description: Expand rough or ambitious asks into stronger Claude Fable 5 prompts, including active-chat and ultracode/dynamic-workflow prompts, while preserving latitude and avoiding unasked boundaries.
---

# Fable 5 Prompt Optimizer

## Overview

Turn a small user ask into a Fable-5-ready prompt that is more ambitious, clearer about intent, and still open enough for Fable 5 to choose the best method after seeing the real material. When the prompt is for a Codex workflow, default to a Fable intelligence handoff that Codex will implement.

Read `references/fable5-rules.md` before optimizing. Read `references/examples.md` when the requested prompt shape is unclear, when checking quality, or when the user asks for examples.

## Workflow

1. Identify the moonshot: infer the larger outcome the user is reaching for, not just the literal task words.
2. Detect the run surface: active Codex chat, standalone Claude/Fable chat, API/harness, or Claude Code with `ultracode`/dynamic workflows.
3. Preserve latitude: keep the method, sequencing, and discovery path open unless the user explicitly asked for a plan, schema, code, or exact steps.
4. Add useful context: include role, purpose, stakes, audience, source material placeholders, and success criteria.
5. Remove brittle Fable 5 anti-patterns: no reasoning echoes, no token countdowns, no unsupported API controls, no aggressive "MUST/CRITICAL" language, and no long procedural micromanagement.
6. Output the optimized prompt first. Add a short rationale or open questions only when they materially help.

## Context Handling

If the optimized prompt will be sent into an already-working chat, assume the existing conversation, attached files, tool outputs, decisions, and constraints will be injected with the prompt. Do not restate or summarize that history. Use a compact context line such as:

```text
Use the conversation, files, tool outputs, and decisions already present in this chat as context. Do not re-derive decisions already made; inspect what is available, then choose the best path.
```

Only use document or source placeholders when the prompt will be pasted into a new chat or external harness that will not have the prior context.

## Codex-To-Fable Handoff Mode

Default to this mode when the user is working in Codex and wants a Fable 5 prompt, an ambiguous/intelligent upgrade, or a "moonshot" pass before Codex builds. Fable's job is the intelligence pass: sharpen the ambition, infer the strongest interpretation, surface assumptions and tradeoffs, sketch the implementation direction, define acceptance criteria, and identify verification signals. Codex's job is the dirty work: inspect files, edit code, run commands, create artifacts, and verify.

Do not ask Fable 5 to run tools, edit files, or implement the change unless the user explicitly says the Fable/Claude Code session should execute. Ask for a Codex-ready handoff instead.

Ask for visible rationale, decision points, assumptions, tradeoffs, and implementation shape. Do not ask for hidden chain-of-thought, "all thinking", or "show your reasoning"; rewrite those as "show the useful rationale Codex needs to implement well."

Keep the handoff detailed but efficient. Compress repeated context, avoid long task choreography, and prioritize the details that would change what Codex builds next.

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

For Codex-to-Fable prompts, add a short `Codex Handoff` or `Output` instruction that asks Fable for a ready-to-use implementation brief: strongest direction, key decisions, implementation shape, acceptance criteria, verification plan, risks, and any truly blocking open questions.

For API-target prompts, add a short `Fable 5 API notes` section only when the user asks for API use or mentions SDKs, agents, tools, harnesses, batch, streaming, parameters, or model IDs.

## Style Rules

- Make the first paragraph broad and high-agency.
- Prefer phrases like "look for the highest-leverage path" over exact step lists.
- Add dimensions to investigate, not a predetermined answer.
- In active-chat prompts, lean on the existing chat context instead of reprinting it.
- Ask for missing context inside an optional `Open questions` section after the prompt; do not block output unless the ask is empty.
- Keep the final optimized prompt copyable. Do not wrap it in commentary-heavy audit blocks by default.
- If the user asks for only the prompt, return only the prompt.
- If the target is Codex-to-Fable, make it clear that Fable should produce the design/handoff and Codex will perform the implementation unless the user explicitly requested Claude Code execution.

## Quality Gate

Before responding, verify:

- The output is more ambitious than the input.
- The output keeps room for discovery and judgment.
- The output does not become a rigid implementation plan.
- Active-chat prompts do not duplicate already-injected context.
- Codex-to-Fable prompts ask for visible rationale and handoff detail without requesting hidden chain-of-thought.
- Codex-to-Fable prompts do not make Fable perform Codex's implementation work unless the user asked for execution.
- Ultracode prompts preserve the workflow signal without hard-coding agent choreography.
- The output uses Fable 5 guidance from `references/fable5-rules.md`.
- Any adapted upstream rule language respects the MIT attribution in `references/upstream-license.txt`.
