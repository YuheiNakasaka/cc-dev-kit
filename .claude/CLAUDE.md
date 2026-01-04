# Claude Code Development Kit

This repository is a template for team development centered around Claude Code.

## Overview

Copy this template to other projects to get:

- Role-based SubAgents (architect, reviewers, developers)
- TDD (Test-Driven Development) support
- Code review workflow
- Consistent rules and workflows

---

## Thinking Language

**Always think in English**, even when the user gives instructions in Japanese or other languages. This ensures consistent reasoning quality and token efficiency.

---

## Development Flow

### SubAgent-First Workflow

**Always start development with SubAgents, not commands.** Claude Code will automatically spawn appropriate SubAgents based on the task context.

#### Phase 1: Analysis & Planning
```
1. orchestrator     → Analyzes complex requests, coordinates workflow
2. architect        → Designs implementation plan, tech selection
3. design-reviewer  → Reviews and approves design
```

**orchestrator** is auto-activated for complex multi-module tasks like:
- "implement full feature"
- "build complete"
- "end-to-end implementation"
- "full stack development"

**architect** plans implementation for requests like:
- "plan implementation"
- "design architecture"
- "how should we implement"

#### Phase 2: Implementation
```
4. tdd-test-writer    → Write tests first (Red phase)
5. tdd-implementer    → Minimal implementation (Green phase)
6. api-developer      → Rails API endpoints
7. frontend-developer → React/ViewComponent development
8. db-designer        → Schema design, migrations
9. ui-designer        → UI design, styling
```

#### Phase 3: Quality Assurance
```
10. code-reviewer → Pre-commit code review (/review)
11. refactorer    → Code quality improvements
12. debugger      → Root cause analysis for issues
```

#### Phase 4: Commit
```
13. /commit "message" → Commit with review confirmation
```

### TDD (Test-Driven Development)

Test-first development is recommended. Request "TDD implementation" to start TDD flow.

1. **Red**: `tdd-test-writer` agent writes test first (verify it fails)
2. **Green**: `tdd-implementer` agent writes minimal implementation
3. **Refactor**: Improve code (keep tests passing)

### Commit Convention

- Commit frequently per feature
- Code review before commit is recommended (`/review`)
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
│   ├── orchestrator/      # Workflow coordinator
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
├── skills/                # Complex skills (with SKILL.md)
│   ├── ui-check/          # UI check skill
│   └── external-systems/  # External system integration
├── commands/              # User-invocable skills (slash commands)
│   ├── review.md          # /review → triggers code-reviewer agent
│   └── commit.md          # /commit → commit with review check
└── .mcp.json              # MCP config (add to .gitignore if contains API keys)
```

---

## Skills (User-Invocable)

Minimal set of slash commands for essential workflows:

| Skill | Description | Triggers SubAgent |
|-------|-------------|-------------------|
| `/review` | Pre-commit code review | code-reviewer |
| `/commit "message"` | Commit with review check | - |
| `/ui-check` | Check UI styles and usability | - (uses Playwright MCP) |

**For all other workflows** (planning, design, TDD, implementation), simply describe what you want to build. Claude Code will automatically spawn the appropriate SubAgents (orchestrator, architect, tdd-test-writer, etc.).

---

## SubAgents

SubAgents are specialized AI agents that handle specific development tasks. **Claude Code automatically spawns appropriate SubAgents based on your request.**

### Primary Entry Points (Start Here)

| Agent | Auto-Activation Triggers | Role |
|-------|-------------------------|------|
| **orchestrator** | "implement full feature", "build complete", "end-to-end", "full stack", "spans multiple modules" | Senior architect & workflow coordinator. Analyzes requirements, breaks down tasks, coordinates other SubAgents |
| **architect** | "plan implementation", "design architecture", "how should we implement" | Designs implementation strategy, identifies critical files, considers trade-offs |

**Best Practice**: For any non-trivial task, simply describe what you want to build. The orchestrator will automatically analyze, plan, and coordinate the appropriate SubAgents.

### Design Phase
- **design-reviewer**: Reviews architect's design plan before implementation
- **modeler**: Domain modeling, business logic organization, design diagrams

### Implementation Phase
- **api-developer**: Rails API endpoints, backend development
- **frontend-developer**: React/ViewComponent, UI implementation
- **db-designer**: Database schema design, migrations
- **ui-designer**: UI design, styling, appearance improvements

### Quality & Review Phase
- **code-reviewer**: Pre-commit code review, checks changes
- **debugger**: Systematic root cause analysis for bugs and errors
- **refactorer**: Code quality improvements, tech debt reduction

### TDD Phase
- **tdd-test-writer**: Writes tests first (Red phase)
- **tdd-implementer**: Minimal implementation to pass tests (Green phase)

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
