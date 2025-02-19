Pattern: Missing assertion

Issue: -

## Description

Each test should include at least one assertion using `expect()`. Tests without assertions may pass without actually verifying any behavior.

## Examples

Example of **incorrect** code:
```javascript
it("should be a test", () => {
  console.log("no assertion");
});

test("should assert something", () => {});
```

Example of **correct** code:
```javascript
it("should be a test", () => {
  expect(value).toBeDefined();
});

test("should assert something", () => {
  expect(result).toBe(true);
});
```