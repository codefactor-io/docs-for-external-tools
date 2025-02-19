Pattern: Invalid expect usage

Issue: -

## Description

The `expect()` function must be called with a single argument and followed by a matcher function. Missing arguments, missing matchers, or incorrect matcher usage will cause tests to fail unexpectedly.

## Examples

Example of **incorrect** code:
```javascript
expect();
expect("something");
expect(value).toBeDefined;
expect(true, false).toBe(true);
```

Example of **correct** code:
```javascript
expect("something").toBe("something");
expect(value).toBeDefined();
expect(Promise.resolve(1)).resolves.toBe(1);
```