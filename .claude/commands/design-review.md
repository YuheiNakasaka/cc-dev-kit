---
description: Call design reviewer to review design strategy
argument-hint: [Design doc path or name (optional)]
---

# Design Review Launch

Use design-reviewer SubAgent to review design strategy.

## Target
$ARGUMENTS

If no argument specified, review the latest design doc under `.claude/tmp/design/`.

## Execution Steps

1. Load design doc
2. Evaluate based on review perspectives
3. Create improvement suggestions
4. Decide approval/rejection

## Output

Report review results and suggest next action (start implementation or redesign).
