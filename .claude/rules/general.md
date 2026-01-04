# General Development Rules

## Git/GitHub Operations
- Use local `gh` command for git/GitHub access, not MCP
- All PR creation, Issue operations, and repository operations should use `gh` command

```bash
# Create PR example
gh pr create --title "Title" --body "Description"

# List issues
gh issue list

# Merge PR
gh pr merge --squash
```

## Commit Convention
- Commit frequently with `git add` and `git commit` for each feature
- Write commit messages in Japanese, describing changes concisely
- Split large changes into smaller commits

## Code Quality
- Always plan implementation with architect before coding
- Get design reviewer approval before implementation
- Code review before commit is recommended
