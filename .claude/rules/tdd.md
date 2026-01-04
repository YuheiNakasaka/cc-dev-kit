# TDD (Test-Driven Development) Rules

## Basic Policy
Test-first development is recommended, but strict Red-Green-Refactor cycle is not enforced.

## Recommended Flow

### 1. Write Test First (Red)
- Express requirements as test cases
- Verify test fails

### 2. Minimal Implementation (Green)
- Write minimal code to pass the test
- Avoid over-implementation

### 3. Refactoring (Refactor)
- Improve code while keeping tests passing
- Remove duplication, improve naming, organize structure

## Test Types
- **Unit Test**: Verify individual methods/classes
- **Integration Test**: Verify component interactions
- **E2E Test**: Verify user scenarios

## Start TDD
Use `/tdd` command to explicitly start TDD flow.
