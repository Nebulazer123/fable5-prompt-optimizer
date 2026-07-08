# Capability Contexts

Use these as selective prompt dimensions. Do not include every row in every prompt; choose only the context that would materially improve the user's ask.

## Skill Or Repo Improvement

Use when the user asks to improve a skill, repo, plugin, workflow, or local capability.

- Entry point: name the supplied path or placeholder and start with the main entry file.
- Context loading: inspect the tree, then read directly referenced resources and files made relevant by the ask.
- Deep pass trigger: widen to all references, scripts, tests, and examples only when the user asks for maximum improvement, a deep audit, or public readiness.
- Claude Code routing: mention `/skills`, `/reload-skills`, skill validation, or Superpowers writing-skills only when the target run should discover, reload, validate, or improve a skill/plugin.
- Quality bar: find leverage, drift, missing validation, brittle wording, stale assumptions, and weak examples.
- Output: strongest diagnosis, changes the builder should make, acceptance criteria, validation plan, and any blocking unknowns.

## Coding, Migration, Or Audit

Use when the ask involves source code, architecture, migrations, bug fixes, refactors, or codebase-wide audits.

- Inspect existing conventions before choosing the implementation shape.
- Identify affected behavior, ownership boundaries, blast radius, and rollback risk.
- Claude Code routing: consider `codebase-memory` for structural discovery, `/code-review` for correctness review, `/simplify` for cleanup, `/security-review` for security-sensitive diffs, `/run` or `/verify` for runtime proof, and `/batch` only for large independent worktree units.
- Prefer the smallest change that satisfies the real goal.
- Ask for verification matched to risk: tests, build, type checks, smoke checks, screenshots, or focused manual checks.
- Keep implementation sequencing flexible unless the user requested a plan.

## Research Or Company Intelligence

Use when the ask involves company, market, competitive, employer, lead, role, or application research.

- Build a source spine from official/current/local evidence before community or secondary sources.
- Search exact names and semantic variants.
- Claude Code routing: use `/deep-research` or `browse` only when source fanout, web fetches, citations, or cross-checking are central to the ask.
- Separate verified facts, plausible inferences, weak signals, gaps, and recommendations.
- Look for small but important tells: wording changes, hiring signals, program pages, docs, pricing, leadership comments, customer language, filings, job posts, and contradiction patterns.
- Label confidence and freshness; do not turn a weak signal into a fact.

## Design, UI, Or Animation

Use when the ask involves visual design, frontend direction, interaction, animation, creative tooling, portfolios, games, demos, or product experience.

- Ask for a taste direction only when not inferable; otherwise choose a strong direction and say why.
- Include audience, emotional tone, information hierarchy, layout density, motion purpose, interaction states, and accessibility.
- Claude Code routing: consider `/dataviz`, `/design-sync`, Framer skills, Remotion guidance, `/run`, or `/verify` only when the project surface makes those capabilities relevant.
- Avoid generic AI-design tropes, filler sections, decorative gradients, and unearned visual effects.
- For animation, describe intent, timing feel, state transitions, feedback, and what motion should clarify.
- Include visual QA: viewport checks, overlap checks, contrast, keyboard/focus behavior, and whether the result matches the intended feel.

## Vision, Documents, Or Analysis Artifacts

Use when the ask includes screenshots, PDFs, slides, spreadsheets, charts, tables, dense images, or document-heavy work.

- Tell the target to inspect the actual visual/document material before deciding.
- Extract evidence from images, tables, charts, filenames, page structure, and captions.
- Ask for uncertainty labels where visual evidence is partial, blurry, cropped, or contradictory.
- Include output review: check claims against the source material and flag anything inferred rather than observed.
- For deliverables, define the reader, decision, and format the output should support.

## Ultracode Or Dynamic Workflows

Use when the user says `ultracode`, asks for dynamic workflows, many subagents, large-scale verification, multi-lane research, big migrations, or cross-checked audits.

- Preserve the `ultracode` signal without forcing a workflow for routine tasks.
- Treat the workflow/orchestrator as coordinator, not the implementation worker.
- Split independent lanes into subagents only when they can produce useful isolated results.
- Let Claude choose the workflow decomposition after inspecting the material; do not prescribe agent counts or a fixed phase script unless the user asked for that.
- Ask for structured summaries from agents rather than raw logs, huge diffs, or copied intermediate output.
- Use verifier or reviewer passes for important claims and completion status.
- Keep final synthesis focused on decisions, evidence, remaining risk, and what the builder should do next.
