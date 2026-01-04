# Pre-Commit Review Rules

## Basic Policy
- Strongly recommend code review before committing changes
- Use `/review` command to request review

## Review Perspectives
1. **Functionality**: Does it meet requirements?
2. **Readability**: Is the code easy to understand?
3. **Maintainability**: Is it easy to modify in the future?
4. **Testing**: Are appropriate tests written?
5. **Security**: Are there any security issues?
6. **Performance**: Are there any performance issues?

## If Review Not Done
- Warning shown at commit time
- Not blocked, but consider doing review

## How to Request Review
```
/review
```
or
```
Please review this code
```
