# Claude Code Development Kit

This repository is a template for team development centered around Claude Code.

## Overview

Copy this template to other projects to get:

- Role-based SubAgents (architect, reviewers, developers)
- TDD (Test-Driven Development) support
- Code review workflow
- Consistent rules and workflows

---

## Development Flow

### Recommended Flow

```
1. /architect [feature]      → Design implementation plan
2. /design-review            → Review design
3. /tdd [feature]            → TDD implementation (Test → Code → Refactor)
4. /review                   → Code review
5. /commit "message"         → Commit with review check
```

### TDD (Test-Driven Development)

Test-first development is recommended. Start with `/tdd` command.

1. **Red**: Write test first (verify it fails)
2. **Green**: Minimal implementation to pass test
3. **Refactor**: Improve code (keep tests passing)

### Commit Convention

- Commit frequently per feature
- Code review before commit is recommended
- Warning shown on commit, but not blocked

---

## Directory Structure

```
.claude/
├── CLAUDE.md              # This file
├── settings.json          # Claude Code settings (Hooks, permissions)
├── tmp/                   # Temp files (not in git)
│   └── design/            # Design docs
├── rules/                 # Auto-applied rules
│   ├── general.md         # General rules
│   ├── tdd.md             # TDD rules
│   ├── commit.md          # Commit rules
│   ├── playwright.md      # Playwright rules
│   ├── ask-user.md        # Confirmation rules
│   └── tmp-files.md       # Temp file rules
├── agents/                # SubAgents
│   ├── architect/         # Architect
│   ├── design-reviewer/   # Design reviewer
│   ├── code-reviewer/     # Code reviewer
│   ├── debugger/          # Debugger
│   ├── refactorer/        # Refactorer
│   ├── api-developer/     # API developer
│   ├── frontend-developer/# Frontend developer
│   ├── db-designer/       # DB designer
│   ├── ui-designer/       # UI designer
│   ├── modeler/           # Domain modeler
│   ├── tdd-test-writer/   # TDD test writer
│   └── tdd-implementer/   # TDD implementer
├── skills/                # Skills
│   ├── ui-check/          # UI check skill
│   └── external-systems/  # External system integration
└── commands/              # Slash commands
    ├── architect.md       # /architect
    ├── design-review.md   # /design-review
    ├── review.md          # /review
    ├── tdd.md             # /tdd
    └── commit.md          # /commit
└── .mcp.json              # MCP config (add to .gitignore if contains API keys)
```

---

## Commands

| Command | Description |
|---------|-------------|
| `/architect [desc]` | Call architect to plan implementation |
| `/design-review` | Run design review |
| `/review` | Run code review |
| `/tdd [desc]` | Start TDD flow |
| `/commit "message"` | Commit with review check |

---

## SubAgents

### Design Phase
- **architect**: Plan implementation, tech selection
- **design-reviewer**: Review and approve design
- **modeler**: Domain modeling, business design

### Implementation Phase
- **api-developer**: Rails API development
- **frontend-developer**: React/ViewComponent development
- **db-designer**: Schema design, migrations
- **ui-designer**: UI design, styling

### Review & Quality Phase
- **code-reviewer**: Pre-commit code review
- **debugger**: Systematic root cause analysis
- **refactorer**: Code quality, tech debt reduction

### TDD Phase
- **tdd-test-writer**: Write tests (Red phase)
- **tdd-implementer**: Minimal implementation (Green phase)

---

## MCP (Model Context Protocol)

MCP config is in `.claude/.mcp.json`.

### Setup (Context7 API Key)

To use Context7, API Key is required.

1. Get API Key from [Context7](https://context7.com/)
2. Add env to context7 section in `.claude/.mcp.json`:

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"],
      "env": {
        "CONTEXT7_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

**Note**: Add `.mcp.json` to `.gitignore` if it contains API keys.

### Available MCP Servers

#### Playwright
UI screenshots, browser automation.

```
mcp__playwright__browser_navigate
mcp__playwright__browser_screenshot
```

**Note**: Always resize screenshots with `magick` before use.

#### Chrome DevTools
Browser DevTools operations.

#### Context7
Access latest OSS docs (Rails, ViewComponent, etc).

```
Use Context7 to check latest ViewComponent docs
```

---

## Git/GitHub

- Use `gh` command (not MCP)
- Create PR: `gh pr create`
- Issues: `gh issue list`, `gh issue create`

---

## Temp Files

Save temp files to `.claude/tmp/`:

- Design docs: `.claude/tmp/design/`
- Screenshots: `.claude/tmp/screenshots/`
- Research notes: `.claude/tmp/research/`

---

## Rules Reference

See `.claude/rules/` for detailed rules:
- @rules/general.md - General rules
- @rules/tdd.md - TDD rules
- @rules/commit.md - Commit rules
- @rules/playwright.md - Playwright rules
- @rules/ask-user.md - Confirmation rules
- @rules/tmp-files.md - Temp file rules
