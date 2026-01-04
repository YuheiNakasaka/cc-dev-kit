# Requirement Confirmation Rules

## Basic Policy
Before planning implementation, use `AskUserQuestion` tool to confirm with the requester if the requirements or specifications have the following issues.

## Cases Requiring Confirmation

### 1. Ambiguity
- When requirements can be interpreted in multiple ways
- When vague expressions like "something like" exist

### 2. Unclear Details
- When technical details are insufficient
- When expected behavior is not clear

### 3. Missing Information
- When edge cases need consideration
- When error handling policy is unclear
- When there are multiple choices and it's hard to decide

## How to Confirm

```
Use AskUserQuestion tool to:
- Ask specific questions
- Present options (with recommendation if possible)
- Add background information
```

## Example
"Let me confirm about authentication method. Do you prefer JWT or session-based?
- JWT (Recommended): Stateless, scalable
- Session: Server-side state management, easy immediate invalidation"
