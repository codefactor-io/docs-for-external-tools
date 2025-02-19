Pattern: `toBe(true)` in test assertions

Issue: -

## Description

Using `toBe(true)` in test assertions is less flexible and may miss other truthy values like non-empty strings or objects. The `toBeTruthy()` assertion provides a more comprehensive check for any truthy value, making tests more robust.

## Examples

Example of **incorrect** code:
```javascript
expect(foo).toBe(true);
expectTypeOf(foo).toBe(true);
```

Example of **correct** code:
```javascript
expect(foo).toBeTruthy();
expectTypeOf(foo).toBeTruthy();
```