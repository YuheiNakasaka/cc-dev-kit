# Claude Code Development Kit

Template for team development with Claude Code: Role-based SubAgents, TDD support, and code review workflow.

---

## Thinking Language

**Always think in English**, even when the user gives instructions in Japanese.

---

## [CRITICAL] Development Flow

**See `@rules/workflow-enforcement.md` for detailed gates and checklists.**

### Quick Reference

```
Phase 1: Planning     → orchestrator/architect → design-reviewer
Phase 2: TDD          → tdd-test-writer (Red) → tdd-implementer (Green)
Phase 3: Review       → code-reviewer → /commit
```

**⛔ NO CODE WITHOUT PLANNING** - You MUST spawn SubAgents before writing any production code.

---

## SubAgents

| Agent | Triggers | Role |
|-------|----------|------|
| **orchestrator** | "implement", "build", multi-file | Workflow coordinator |
| **architect** | ANY code changes | Design strategy |
| **design-reviewer** | After architect | Approve design |
| **tdd-test-writer** | New features | Write tests first (Red) |
| **tdd-implementer** | After tests fail | Minimal implementation (Green) |
| **code-reviewer** | Before commit, `/review` | Code review |
| **debugger** | "fix bug", "debug" | Root cause analysis |
| **refactorer** | "refactor", "improve" | Code quality |
| **api-developer** | Rails API | Backend endpoints |
| **frontend-developer** | React/ViewComponent | UI implementation |
| **db-designer** | Schema changes | Database design |
| **ui-designer** | Styling | UI/appearance |
| **modeler** | Domain design | Business logic organization |

---

## Commands (Slash Commands)

| Command | Description |
|---------|-------------|
| `/review` | Pre-commit code review |
| `/commit "msg"` | Commit with review check |

---

## Skills (Domain Knowledge)

Skills provide domain-specific knowledge and tooling. Automatically invoked based on context.

| Skill | Description |
|-------|-------------|
| `ui-check` | UI verification with Playwright MCP |
| `external-systems` | External system integration guide |
| `code-review-guideline` | Code review guidelines |

---

## Rules Reference

See `.claude/rules/` for detailed rules:

- `@rules/workflow-enforcement.md` - **[CRITICAL]** Development gates and checklists
- `@rules/general.md` - Git/GitHub, commit convention
- `@rules/tdd.md` - TDD cycle
- `@rules/commit.md` - Pre-commit review
- `@rules/playwright.md` - Screenshot resize
- `@rules/ask-user.md` - Requirement confirmation
- `@rules/tmp-files.md` - Temp file location (`.claude/tmp/`)

---

## Quick Links

- **Design docs**: `.claude/tmp/design/`
- **MCP config**: `.mcp.json`
