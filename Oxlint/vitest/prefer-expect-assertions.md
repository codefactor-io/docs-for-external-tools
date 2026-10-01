Pattern: Missing assertion count

Issue: -

## Description

Without explicit assertion counts, tests with asynchronous code,
callbacks, or loops may pass even if some `expect` calls are never
reached, silently hiding bugs.

## Examples

Example of **incorrect** code:
```javascript
test("no assertions", () => {
  // ...
});
test("assertions not first", () => {
  expect(true).toBe(true);
  // ...
});
```

Example of **correct** code:
```javascript
test("with assertion count", () => {
  expect.assertions(1);
  expect(true).toBe(true);
});
test("with hasAssertions", () => {
  expect.hasAssertions();
  expect(true).toBe(true);
});
```
