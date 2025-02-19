Pattern: Missing error message

Issue: -

## Description

Using `toThrow()` or `toThrowError()` without an error message makes it harder to identify what error was expected. Always include an error message to make test failures more descriptive.

## Examples

Example of **incorrect** code:
```javascript
expect(() => fn()).toThrow();
expect(() => fn()).toThrowError();
await expect(promise()).rejects.toThrow();
```

Example of **correct** code:
```javascript
expect(() => fn()).toThrow("Invalid input");
expect(() => fn()).toThrowError("User not found");
await expect(promise()).rejects.toThrow("Network error");
```