Pattern: Use of restricted matcher

Issue: -

## Description

Some Jest matchers may be restricted to enforce better testing practices or maintain consistency across test suites. Alternative matchers may be suggested based on project requirements.

## Examples

Example of **incorrect** code:
```javascript
expect(value).toBeFalsy();
await expect(promise).resolves.toBe(true);
expect(mock).not.toHaveBeenCalledWith("param");
```

Example of **correct** code:
```javascript
expect(value).toBe(false);
await expect(promise).rejects.toThrow();
expect(mock).toHaveBeenCalledWith("expectedParam");
```