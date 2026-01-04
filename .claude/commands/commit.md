---
description: Create commit with review confirmation
argument-hint: [Commit message]
allowed-tools: Bash(git add:*), Bash(git commit:*), Bash(git status:*), Bash(git diff:*)
---

# Commit with Review Confirmation

Confirm code review status before creating commit.

## Commit Message
$ARGUMENTS

## Execution Steps

### 1. Check Changes

```bash
git status
git diff --staged
```

### 2. Review Confirmation

Has code review been done?

- If done: Create commit
- If not done: Recommend running `/review`

### 3. Create Commit

If review done, or continuing without review:

```bash
git add -A
git commit -m "$ARGUMENTS"
```

## Notes

- Warning shown if review not done
- Not forcibly blocked (respect developer judgment)
- Small changes or obvious fixes can skip review

## Recommended Flow

```
Code changes → /review → Fix → /commit "message"
```
