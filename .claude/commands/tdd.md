---
description: Start TDD (Test-Driven Development) flow
argument-hint: [Feature description to implement]
---

# TDD Development Flow Launch

Start TDD Red-Green-Refactor cycle.

## Target Feature
$ARGUMENTS

## Flow

### Phase 1: Red (Test Creation)
Use tdd-test-writer SubAgent to create failing tests.

1. Express requirements as test cases
2. Create test code
3. Verify tests fail

### Phase 2: Green (Implementation)
Use tdd-implementer SubAgent to create minimal implementation to pass tests.

1. Read and understand tests
2. Create minimal implementation
3. Verify tests pass

### Phase 3: Refactor (Refactoring)
Improve code while maintaining tests.

1. Remove duplication
2. Improve naming
3. Organize structure
4. Verify tests pass

## Execution Method

Execute each phase in order with verification between phases.

```
Phase 1 (Red) → Verify test failure → Phase 2 (Green) → Verify test success → Phase 3 (Refactor) → Verify test success
```

## Notes

- Each phase is handled by independent SubAgent
- Test writer works without knowing implementation
- Implementer doesn't add features not in tests
