---
description: Call code reviewer to execute code review
argument-hint: [File path (optional)]
allowed-tools: Bash(git diff:*), Bash(git status:*), Read, Glob, Grep
---

# Code Review Launch

Use code-reviewer SubAgent to execute code review.

## Target
$ARGUMENTS

If no argument specified, review current changes (git diff).

## Pre-check

```bash
git status
git diff --staged
git diff
```

## Execution Steps

1. Understand changes
2. Evaluate based on review perspectives
3. Organize issues
4. Determine overall evaluation

## Output

Report review results and present commit decision.

- **LGTM**: Ready to commit
- **Needs Changes**: Re-review after fixes
- **Needs Discussion**: Additional discussion required
