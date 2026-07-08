# Contributing

Thanks for improving Fable 5 Prompt Optimizer.

## Good Contributions

- Improve Fable 5 prompt quality without making the skill more rigid.
- Add examples that preserve user intent and leave room for discovery.
- Tighten implementation-handoff behavior.
- Clarify `ultracode` and dynamic-workflow guidance.
- Remove outdated or unsupported model/API guidance.

## Before Opening A Pull Request

1. Create a branch from `main`.
2. Make the smallest useful change.
3. Validate the skill:

```bash
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py .
```

4. Check for accidental local paths or secrets:

```bash
rg -n "Users/|api[_-]?key|token|secret|password" .
```

5. Update `README.md` or `references/examples.md` if behavior changes.

## Pull Request Checklist

- The skill still outputs the optimized prompt first.
- The result stays ambitious without becoming a rigid implementation plan.
- Implementation-handoff prompts ask for a handoff, not hidden chain-of-thought.
- Attribution in `NOTICE.md` and `references/upstream-license.txt` remains intact.
- Validation passes locally.
