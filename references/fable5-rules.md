# Fable 5 Prompt Rules

Sources: adapted from the MIT-licensed `CheswickDEV/claude-fable-5-prompt-optimizer` and updated against Anthropic documentation available on July 8, 2026. See `upstream-license.txt`.

## Core Model Posture

- Claude Fable 5 is built for high-difficulty, ambiguous, long-horizon work. Prompts should make room for the model to scope, inspect, choose a path, and self-verify.
- Skills and prompts written for earlier Claude models can be too prescriptive for Fable 5. Prefer short, high-leverage instructions over long behavior inventories.
- Give the reason behind the request. Fable 5 tends to perform better when it knows the larger task, audience, stakes, and what the output enables.
- Use `high` effort as the default API posture. Reserve `xhigh` or `max` for the most capability-sensitive work; use lower effort for routine tasks.

## Keep The Ask Moonshot

When expanding a rough ask, increase ambition without freezing the implementation:

- Add a stronger role and objective.
- Add stakes: why the work matters and what failure would miss.
- Add a wider exploration frame: hidden assumptions, leverage points, counterexamples, system effects, and surprising alternatives.
- Add success criteria that describe a good answer, not exact steps to produce it.
- Add placeholders for real material instead of inventing facts.

Use this guardrail when the prompt risks becoming too specific:

> Do not over-decide the method. Inspect the real material first, then choose the path that best fits what you find.

## PromptBuilder-Inspired Structure

PromptBuilder's public Claude generator shows a useful generic pattern: broad role/objective, context, and structured sections. Borrow the visible pattern, not any hidden server-side prompt.

Useful sections:

- `Role & Objective`
- `Context`
- `Ambition`
- `What To Explore`
- `Output`
- `Boundaries`

Avoid generic PromptBuilder weaknesses:

- Do not turn every ask into a conventional "comprehensive audit."
- Do not add generic bullets that could fit any project.
- Do not make the prompt model-agnostic when the user asked for Fable 5.

## Fable 5 Anti-Patterns To Remove

Remove or rewrite:

- "Show your reasoning", "explain your thinking", "think step by step in the answer", or any request to reproduce internal reasoning. This can trigger the Fable 5 `reasoning_extraction` refusal category.
- Token/context countdown instructions. They can encourage early stopping or handoff behavior.
- `temperature`, `top_p`, `top_k`, assistant prefill, `thinking: disabled`, and `budget_tokens` recommendations. These are unsupported or wrong for Fable 5-era API use.
- Aggressive trigger language such as "CRITICAL", "MUST", "never be lazy", or forced status rituals unless the user explicitly needs strict compliance wording.
- Detailed execution sequences when the user wanted a prompt, not an implementation plan.

## Long Or Agentic Prompts

For coding, research, or long-running agent prompts, include lightweight autonomy and verification guidance:

- "When you have enough information to act, act."
- "Pause only for destructive actions, real scope changes, or input only the user can provide."
- "Before reporting progress, audit each claim against evidence from this session."
- "Use subagents or independent passes for separable research or verification when available."

Keep this guidance compact. Fable 5 does not need every possible case enumerated.

## Active Chat And Ultracode

For prompts that will be sent into an already-running chat, assume the chat history and attached materials are available to the target model. Do not echo the whole history back into the optimized prompt. Add only a compact instruction to use the conversation, files, tool outputs, and prior decisions already present.

In Claude Code, `ultracode` is both a prompt keyword and a session setting. It pairs `xhigh` effort with dynamic workflow orchestration for substantive tasks. A dynamic workflow is a JavaScript orchestration script that can fan work out to many subagents, keep intermediate results outside the main context, and cross-check findings before synthesis.

Use workflow language only when the user asks for `ultracode`, workflows, many subagents, or a task large enough to benefit from scripted orchestration: codebase-wide audits, large migrations, cross-checked research, repeated verification loops, or multi-angle planning. Keep the prompt high-level; let Fable 5 decide the decomposition after inspecting the real material.

## Codex-To-Fable Handoffs

When the prompt is being written for use inside a Codex workflow, Fable 5 is usually the high-intelligence design pass and Codex is the builder. The optimized prompt should ask Fable 5 to produce the material Codex needs to implement well:

- The strongest interpretation of the ask.
- The key assumptions and decision points.
- The implementation shape, not line-by-line instructions.
- Acceptance criteria and verification signals.
- Risks, tradeoffs, and truly blocking unknowns.

Avoid asking Fable 5 to edit files, run commands, or implement unless the user explicitly says the target session should execute. Also avoid "write all your thinking" language. Ask for visible rationale and decision support instead of hidden chain-of-thought.

For active Codex chats, do not repeat the chat history. Use a compact context instruction and let Fable infer from the injected context:

> Use the existing conversation, files, tool outputs, and decisions as context. Produce the Codex-ready intelligence handoff, not the implementation. Show the useful rationale, tradeoffs, and acceptance criteria Codex needs to build the right thing.

## Output Defaults

Default answer shape:

1. Optimized prompt first.
2. Tiny `Why this is stronger` note only when helpful.
3. `Open questions` only for missing details that would materially improve use.

If the user asks for API use, include:

- model: `claude-fable-5`
- effort: usually `high`
- max_tokens: generous enough for thinking plus answer
- streaming: yes for long outputs or agentic runs
- fallback note for cyber, bio, or reasoning-extraction-risk domains

Do not include API notes for normal chat prompts.
