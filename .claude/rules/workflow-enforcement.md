# [CRITICAL] Workflow Enforcement Rules

## MANDATORY: SubAgent-First Development

**YOU MUST NOT write or modify production code without completing the following gates.**

This is non-negotiable. Violations break team workflow and bypass quality controls.

---

## Gate 1: Planning (REQUIRED before ANY implementation)

### For ANY task that modifies code:

1. **MUST spawn `orchestrator` or `architect` SubAgent FIRST**
   - Use `orchestrator` for: multi-file changes, new features, cross-module work
   - Use `architect` for: single-module changes, refactoring, bug fixes requiring design decisions

2. **MUST save design document** to `.claude/tmp/design/[feature-name].md`

3. **MUST get explicit user approval** before proceeding to implementation

### Blocking Conditions:
- DO NOT use `Write` or `Edit` tools on source files until planning is complete
- DO NOT skip planning even for "simple" changes
- DO NOT implement while "thinking about" the design

---

## Gate 2: Design Review (REQUIRED before implementation)

1. **MUST spawn `design-reviewer` SubAgent** after architect completes design
2. **MUST address all design review feedback** before proceeding
3. **If design is rejected**: Return to architect, do not proceed

---

## Gate 3: TDD Implementation (REQUIRED for new features)

For any new functionality:

1. **MUST spawn `tdd-test-writer` SubAgent FIRST** to write failing tests
2. **MUST verify tests fail** before writing implementation
3. **MUST spawn `tdd-implementer` SubAgent** for minimal implementation
4. **MUST verify tests pass** before considering implementation complete

### Exception:
- Bug fixes with existing test coverage may skip test-writing phase
- Configuration changes may skip TDD

---

## Gate 4: Code Review (REQUIRED before commit)

1. **MUST spawn `code-reviewer` SubAgent** (or use `/review` command)
2. **MUST address all Critical and High priority issues**
3. **MUST NOT commit with unresolved Critical issues**

---

## Workflow Enforcement Checklist

Before writing ANY production code, verify:

```
[ ] Planning SubAgent spawned (orchestrator/architect)
[ ] Design document created in .claude/tmp/design/
[ ] User approved the design
[ ] design-reviewer approved (for non-trivial changes)
[ ] Tests written first (tdd-test-writer)
[ ] Tests verified to fail
```

Before committing, verify:

```
[ ] Implementation complete (tdd-implementer)
[ ] All tests pass
[ ] code-reviewer completed review
[ ] Critical issues resolved
```

---

## Auto-Spawn Triggers

When you detect these patterns, IMMEDIATELY spawn the appropriate SubAgent:

| User Request Pattern | MUST Spawn | Reason |
|---------------------|------------|--------|
| "implement", "add feature", "create", "build" | `orchestrator` | Multi-phase coordination needed |
| "fix bug", "resolve issue", "debug" | `debugger` → `architect` | Root cause analysis first |
| "refactor", "improve", "clean up" | `architect` → `refactorer` | Design before changes |
| "update", "modify", "change" | `architect` | Understand impact first |

---

## Violation Response

If you find yourself about to write code without completing gates:

1. **STOP immediately**
2. **Inform the user** that workflow gates are required
3. **Spawn the appropriate planning SubAgent**
4. **Resume only after gates are satisfied**

---

## Examples

### CORRECT Flow:
```
User: "Add user authentication feature"
Claude: Spawns orchestrator
        → orchestrator creates plan, spawns architect
        → architect designs, saves to .claude/tmp/design/auth-feature.md
        → design-reviewer approves
        → tdd-test-writer writes tests
        → tdd-implementer implements
        → code-reviewer reviews
        → /commit
```

### INCORRECT Flow (FORBIDDEN):
```
User: "Add user authentication feature"
Claude: Immediately starts writing auth code  ← VIOLATION
```

### INCORRECT Flow (FORBIDDEN):
```
User: "This is a simple change, just add a field"
Claude: Skips planning, writes code directly  ← VIOLATION
```
