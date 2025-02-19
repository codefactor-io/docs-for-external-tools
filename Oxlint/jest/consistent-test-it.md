Pattern: Inconsistent test declaration

Issue: -

## Description

Using a mix of `test()` and `it()` in test suites reduces consistency and readability. Test declarations should use the same function throughout the codebase.

## Examples

Example of **incorrect** code:
```javascript
test("first test", () => {
  expect(value).toBe(true);
});

it("second test", () => {
  expect(value).toBe(false);
});
```

Example of **correct** code:
```javascript
test("first test", () => {
  expect(value).toBe(true);
});

test("second test", () => {
  expect(value).toBe(false);
});
```