---
description: Call architect to plan implementation strategy
argument-hint: [Feature description]
---

# Architect Launch

Use architect SubAgent to plan implementation strategy for the following feature.

## Target Feature
$ARGUMENTS

## Execution Steps

1. Analyze requirements, confirm unclear points with `AskUserQuestion`
2. Investigate existing codebase
3. Plan implementation strategy
4. Create design doc in `.claude/tmp/design/`
5. Prepare for design review

## Output

Create design doc and recommend design review (`/design-review`).
