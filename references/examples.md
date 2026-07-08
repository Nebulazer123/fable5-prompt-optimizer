# Examples

Use these as behavior examples, not as templates to copy mechanically.

## Example 1: Portfolio Moonshot

Raw ask:

```text
make me a wild plan to fix my portfolio
```

Better Fable 5 prompt:

```text
Role & Objective
You are a senior portfolio strategist and product-minded editor. Help me transform my portfolio from a collection of artifacts into a sharper proof system for the kind of work I want to be trusted with.

Context
I may have existing projects, drafts, screenshots, resumes, case studies, and half-finished ideas. Treat the portfolio as a system: audience, evidence, navigation, story, credibility, and conversion.

Ambition
Look for the highest-leverage transformation, not just surface polish. Identify what would make the portfolio feel unusually clear, specific, and hard to dismiss.

What To Explore
- Which work should become the center of gravity.
- Where the current story undersells the strongest evidence.
- What is missing, redundant, confusing, or too generic.
- What a hiring manager or collaborator would need to believe after five minutes.
- Unexpected formats or interactions that could make the work more memorable.

Output
Give me a portfolio transformation brief with the strongest thesis, the main opportunities, and a small set of decisive next moves. Keep the method flexible: inspect the real material before choosing exact fixes.

Boundaries
Do not over-decide the implementation before seeing the portfolio. Do not turn this into a generic checklist.
```

## Example 2: AI Research Thing

Raw ask:

```text
help me make an ai research thing
```

Better Fable 5 prompt:

```text
Role & Objective
You are a research designer helping me turn a vague AI idea into a serious, testable research artifact.

Context
I have an early intuition, not a finished thesis. The goal is to uncover a promising research direction, define what would count as evidence, and shape it into something another smart person could evaluate.

Ambition
Push beyond a normal brainstorm. Look for an angle that is useful, surprising, and specific enough to test, while still leaving room for discovery.

What To Explore
- The core question hiding inside the rough idea.
- Why it matters now and who would care.
- What existing assumptions it challenges.
- What small experiment, dataset, prototype, or comparison could create evidence.
- What would make the result publishable, portfolio-worthy, or practically useful.

Output
Produce a research concept brief: thesis candidates, strongest direction, evidence plan, risks, and next artifact to build. Choose the path after inspecting whatever context I provide.

Boundaries
Do not invent literature claims. Do not lock the project into a narrow method before seeing the actual idea and available material.
```

## Example 3: Codex-Specific Implementation Handoff

Raw ask:

```text
turn this into a Fable 5 prompt for a coding agent, but Codex will build it after
```

Better Fable 5 prompt:

```text
Role & Objective
Act as the architecture and implementation-intelligence pass for a Codex coding workflow. Upgrade the user's rough request into the strongest Codex-ready handoff: what should be built, why it matters, what tradeoffs matter, and how Codex should know the result is good.

Context
Use the existing conversation, files, tool outputs, repo clues, and decisions already present as context. Codex will inspect files, edit code, run commands, and verify after your answer, so do not restate the whole chat or try to implement the change yourself.

Ambition
Find the highest-leverage interpretation of the request. Keep enough ambiguity for Codex to adapt after inspecting the real code, but make the target outcome and quality bar sharp.

What To Explore
- Existing patterns and ownership boundaries.
- The true behavioral surface affected by the change.
- The implementation shape that is most likely to fit the codebase.
- The acceptance criteria that would separate a real fix from a cosmetic one.
- The verification path Codex should use for the risk level.
- Risks, tradeoffs, or open questions that could change the build.

Output
Return a concise but detailed Codex handoff: strongest direction first, then key decisions, implementation shape, acceptance criteria, verification plan, and any truly blocking questions. Show useful rationale and tradeoffs, not hidden chain-of-thought. Do not try to implement; Codex should choose the final path after inspecting the repo.
```

## Example 4: PromptBuilder-Style Analysis Without Generic Drift

Visible PromptBuilder-style result pattern:

```text
Role & Objective
You are a deep-intelligence system tasked with conducting a comprehensive, open-ended audit...

Context
The system is designed to improve accuracy through better data...
```

Fable 5 version with more latitude:

```text
Role & Objective
You are a deep diagnostic partner helping me understand where this system could become meaningfully better, not just where it appears broken.

Context
I will provide the real system materials, notes, outputs, or examples. Treat them as the source of truth. The system may contain hidden inconsistencies, weak evaluation signals, accidental incentives, or improvements that look good but do not actually increase quality.

Ambition
Look for the few observations that would change what we build next. Favor high-leverage discoveries over a broad inventory of minor issues.

What To Explore
- Hidden failure modes and edge cases.
- Places where apparent progress is not real progress.
- Missing measurements or weak proxies.
- Surprising redesign opportunities.
- What evidence would separate a real improvement from a cosmetic one.

Output
Give me a diagnostic brief with the strongest findings, the most important uncertainty, and the next artifact or experiment that would clarify it.

Boundaries
Do not decide the exact repair plan before inspecting the material. Do not fill gaps with invented facts.
```

## Example 5: Active Chat Ultracode Prompt

Raw ask:

```text
ultracode this whole chat and make the portfolio fix way more ambitious with subagents
```

Better Fable 5 prompt:

```text
Role & Objective
Act as the high-agency portfolio strategy pass for a Claude Code workflow. Use the conversation, files, tool outputs, and decisions already present in this chat as context. Turn the portfolio work into a much more ambitious, evidence-driven improvement pass without losing the user's actual goals.

Context
Use the existing chat context as the source material. Do not restate the chat history or re-derive decisions already made. Inspect the real materials that are available, then choose the path that best fits what you find.

Ambition
Look for the highest-leverage way to make the portfolio harder to dismiss: stronger proof, sharper positioning, clearer artifacts, better navigation, and a more memorable interaction model if the materials support it.

Workflow Mode
Use ultracode/dynamic workflows if the task is large enough to benefit from scripted orchestration. Fan out independent work to focused subagents, cross-check important findings, and synthesize the strongest path back into one coherent plan or implementation.

What To Explore
- Which existing evidence should become the center of gravity.
- Where the current story undersells the strongest proof.
- What a reviewer should understand after five minutes.
- Which changes are cosmetic versus genuinely career-leveraging.
- What should be built, rewritten, removed, or tested next.

Output
Give the strongest portfolio transformation direction first, then the key findings and the next concrete moves. Keep the method flexible: choose the decomposition and verification path after inspecting the actual chat context and files.
```

## Example 6: Fable Before Codex Builds

Raw ask:

```text
make this way more ambitious for Fable 5 before Codex builds it
```

Better Fable 5 prompt:

```text
Role & Objective
Act as the high-intelligence design pass before Codex implements. Transform the rough ask into a stronger, more ambitious implementation brief without locking Codex into a brittle plan.

Context
Use the existing chat, attached files, tool outputs, and decisions as context. Codex will do the repo inspection, implementation, commands, artifact creation, and verification after your answer.

Ambition
Infer the bigger outcome the user is actually reaching for. Raise the quality bar, identify the leverage points, and make the work feel more serious, specific, and useful without adding unasked boundaries.

What To Explore
- The strongest interpretation of the user's goal.
- What would make the result meaningfully better than the obvious version.
- Hidden constraints, assumptions, and tradeoffs Codex should respect.
- The implementation shape that seems most promising before repo inspection.
- The acceptance criteria and verification signals Codex should use.

Output
Return the Codex-ready handoff first: recommended direction, key decisions, implementation shape, success criteria, verification plan, and any truly blocking unknowns. Show the useful rationale Codex needs, but do not write hidden chain-of-thought or perform the implementation.
```

## Example 7: New Chat Skill Improvement Prompt

Raw ask:

```text
i want you to improve my company-intelligent-research skill as much as possible
```

Better Fable 5 prompt:

```text
Role & Objective
Act as the high-intelligence audit and design pass before Codex edits a local agent skill. Upgrade the `company-intelligent-research` skill so it can perform deeper, more logical, source-backed company research: broad enough to find small but important signals, disciplined enough to distinguish facts from weak but meaningful inferences, and practical enough for Codex to implement and validate.

Target
Skill path: `~/.codex/skills/company-intelligent-research/SKILL.md`

Context Loading
Use the target path/source material below as the starting point. Start by reading the target `SKILL.md`, then inspect the skill folder tree. Read the reference files, scripts, and tests that the entry file points to or that become relevant to this improvement pass. Because this is a maximum-improvement audit, widen to the full skill folder if small details could reveal missing opportunities.

Ambition
Look for improvements that make the skill better at deep evidence work, not just cleaner wording. Pay attention to weak signals, source routing, confidence labeling, contradiction handling, search breadth, provider escalation, local evidence, readiness checks, output contracts, and ways to prevent shallow or unsupported conclusions.

What To Explore
- Where the current workflow under-searches, over-trusts snippets, or misses small but important tells.
- How the skill should separate verified facts, plausible inferences, weak signals, gaps, and recommendations.
- Whether the reference files, scripts, tests, and output contracts reinforce each other or drift.
- Which changes would make Codex implement the skill upgrade safely without turning it into a bloated checklist.
- What validation would prove the upgraded skill actually performs deeper research.

Output
Return a Codex-ready handoff: strongest diagnosis, highest-leverage improvements, specific files Codex should inspect or edit, acceptance criteria, validation plan, and any blocking unknowns. Show useful rationale and tradeoffs, not hidden chain-of-thought. Do not edit files yourself; Codex will implement after your handoff.
```

## Example 8: UI And Animation Moonshot

Raw ask:

```text
make this UI/animation pass way more ambitious
```

Better Fable 5 prompt:

```text
Role & Objective
Act as a product-minded visual design and motion direction pass before Codex implements. Upgrade the rough UI/animation ask into a stronger creative brief that raises the quality bar without dictating every implementation detail.

Context
Use the existing product context, screenshots, codebase clues, and design constraints as source material. If visual assets or running UI are available, inspect them before deciding what kind of motion or interaction polish would actually help.

Ambition
Look for the highest-leverage way to make the interface feel more intentional, usable, and memorable. Treat animation as communication: it should clarify state, hierarchy, causality, pacing, or delight, not decorate the page.

What To Explore
- The strongest visual direction for the product and audience.
- Where hierarchy, spacing, density, typography, or color are weakening the experience.
- Which interactions need hover, active, disabled, loading, focus, transition, or empty-state treatment.
- What motion should communicate, how it should feel, and where stillness is better.
- Accessibility, viewport, overlap, contrast, and reduced-motion checks Codex should verify.

Output
Return a Codex-ready design handoff: recommended direction, interaction and motion priorities, implementation shape, acceptance criteria, visual QA plan, and risks. Keep room for Codex to adapt after inspecting the real UI.
```

## Example 9: Claude Code Repo Review With Selective Commands

Raw ask:

```text
review this diff and tell Codex what to fix
```

Better Fable 5 prompt:

```text
Role & Objective
Act as the high-signal review and implementation-intelligence pass before Codex edits. Inspect the current diff and identify the issues that would most change correctness, maintainability, or user impact.

Context
Use the active session context and current repo state as source material. If available, use project code-intelligence tools for structural discovery and review-oriented commands only where they materially improve the review.

Ambition
Look beyond obvious style notes. Find behavior regressions, brittle assumptions, missing tests, weak abstractions, and places where the diff fights existing project patterns.

What To Explore
- The intended behavior versus what the diff actually changes.
- Call paths, ownership boundaries, and likely blast radius.
- Correctness risks, simplification opportunities, and test gaps.
- Whether a targeted `/code-review`, `/simplify`, or `/security-review` pass would add useful evidence.
- What Codex should verify before calling the fix done.

Output
Return a Codex-ready repair brief: prioritized findings, why each matters, the likely implementation shape, acceptance criteria, and verification signals. Keep the command/tool suggestions selective; do not turn this into a generic checklist.
```

## Example 10: Research With Source Fanout

Raw ask:

```text
deeply research this company and find weak signals
```

Better Fable 5 prompt:

```text
Role & Objective
Act as a source-backed company intelligence pass. Build the strongest useful read on the company from current evidence, including small tells that may matter even when the evidence is incomplete.

Context
Use the company name, links, files, and active chat context already available. Use source-fanout research only if it materially improves freshness, coverage, or contradiction checks.

Ambition
Go beyond a normal company summary. Look for strategic shifts, hiring and product signals, customer language, pricing or docs changes, leadership comments, market pressure, and inconsistencies across sources.

What To Explore
- Verified facts from official or primary sources.
- Plausible inferences from weak but meaningful signals.
- Contradictions, stale claims, and missing evidence.
- Whether `/deep-research` or browser-based source inspection would materially improve confidence.
- What matters for the user's likely next decision.

Output
Return a concise intelligence brief with facts, inferences, weak signals, confidence labels, source freshness, contradictions, and recommended next moves. Do not inflate weak evidence into certainty.
```

## Example 11: Framer And Animation Upgrade

Raw ask:

```text
improve my framer project and make the animations better
```

Better Fable 5 prompt:

```text
Role & Objective
Act as the product-minded Framer design and motion pass before implementation. Upgrade the project so the page feels more intentional, easier to read, and more memorable without adding decorative motion that does not serve the experience.

Context
Use the active project context, existing design system, canvas structure, assets, and any screenshots already available. If Framer project skills are available, use them for project-aware inspection and recommendations.

Ambition
Look for the few changes that would most improve perceived quality: hierarchy, spacing, typography, interaction states, motion pacing, responsive behavior, and conversion clarity.

What To Explore
- Which sections need structural design changes versus light polish.
- Where animation should clarify state, hierarchy, causality, or feedback.
- Hover, active, focus, loading, empty, and reduced-motion states.
- Whether `/run`, `/verify`, visual QA, or Framer-specific inspection would provide useful proof.
- Risks from over-animation, inaccessible contrast, layout overlap, or fragile component constraints.

Output
Return a Codex-ready Framer handoff: recommended design direction, motion priorities, implementation shape, acceptance criteria, and visual QA checks. Mention only the project capabilities that actually help this task.
```

## Example 12: Prepared Packet Before Fable Review

Raw ask:

```text
review this repo before I send it to Fable
```

Codex preflight:

```text
Create a packet at `work/fable5-context/repo-review.md` before sending the prompt. Include the user's ask, current objective, target paths, relevant files, current diff/status, quick validation results or why they were not run, known gaps, and what Fable should decide.
```

Better Fable 5 prompt:

```text
Role & Objective
Act as the high-intelligence review and strategy pass before the builder continues implementation. Use the prepared state to identify the highest-leverage issues, missing context, and next moves.

Context Packet
Use this prepared context packet as the starting point: `work/fable5-context/repo-review.md`.
Treat it as a state snapshot. Inspect only what is necessary to make the review and handoff stronger.

Ambition
Do not merely summarize the repo. Find the few judgments that would change what the builder should do next: hidden risks, weak assumptions, missing validation, unclear ownership boundaries, or opportunities to simplify the next implementation pass.

What To Explore
- Whether the current state is ready for review or still missing a cheap checkpoint.
- Which findings are evidence-backed versus uncertain.
- Which incomplete items should block the next build step and which should be recorded as known gaps.
- What the builder should do after your handoff.

Output
Return an implementation-ready review brief: highest-leverage findings, decision points, recommended next move, acceptance criteria, validation plan, and any gaps the builder should resolve. Show useful rationale and tradeoffs, not hidden chain-of-thought. Do not perform the implementation.
```
