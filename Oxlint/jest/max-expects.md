Pattern: Too many assertions

Issue: -

## Description

Having too many assertions in a single test indicates the test may be mixing multiple objectives. Tests should be focused on verifying a single behavior or feature to maintain clarity and ease of debugging.

## Examples

Example of **incorrect** code:
```javascript
test("should not pass", () => {
  expect(value1).toBeDefined();
  expect(value2).toBeDefined();
  expect(value3).toBeDefined();
  expect(value4).toBeDefined();
  expect(value5).toBeDefined();
  expect(value6).toBeDefined(); // Exceeds maximum of 5
});
```

Example of **correct** code:
```javascript
test("should pass", () => {
  expect(value1).toBeDefined();
  expect(value2).toBeDefined();
  expect(value3).toBeDefined();
});
```