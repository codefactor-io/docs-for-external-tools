Pattern: Too many assertions

Issue: -

## Description

Tests with many different assertions are likely mixing multiple objectives.
It is generally better to have a single objective per test to ensure that when a test fails,
the problem is easy to identify.

## Examples

Example of **incorrect** code:
```javascript
test("should not pass", () => {
  expect(true).toBeDefined();
  expect(true).toBeDefined();
  expect(true).toBeDefined();
  expect(true).toBeDefined();
  expect(true).toBeDefined();
  expect(true).toBeDefined();
});

it("should not pass", () => {
  expect(true).toBeDefined();
  expect(true).toBeDefined();
  expect(true).toBeDefined();
  expect(true).toBeDefined();
  expect(true).toBeDefined();
  expect(true).toBeDefined();
});
```
