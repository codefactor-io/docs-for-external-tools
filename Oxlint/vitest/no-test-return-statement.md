Pattern: Return statement inside test

Issue: -

## Description

Tests in Jest should be void and not return values.
If you are returning Promises then you should update the test to use
`async/await`.

## Examples

Example of **incorrect** code:
```javascript
test("one", () => {
  return expect(1).toBe(1);
});
```

Example of **correct** code:
```javascript
test("one", () => {
  expect(1).toBe(1);
});
```
