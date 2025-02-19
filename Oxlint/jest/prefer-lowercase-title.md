Pattern: Capitalized test title

Issue: -

## Description

Test titles should begin with lowercase letters to maintain consistency and provide more readable test failures. Exceptions can be configured for specific test functions or allowed prefixes.

## Examples

Example of **incorrect** code:
```javascript
it("Adds numbers correctly", () => {
  expect(add(1, 2)).toBe(3);
});

test("Returns valid data", () => {
  expect(getData()).toBeDefined();
});
```

Example of **correct** code:
```javascript
it("adds numbers correctly", () => {
  expect(add(1, 2)).toBe(3);
});

test("returns valid data", () => {
  expect(getData()).toBeDefined();
});
```