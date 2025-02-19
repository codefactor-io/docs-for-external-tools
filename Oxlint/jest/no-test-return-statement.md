Pattern: Return statement in test

Issue: -

## Description

Tests should not return values. If dealing with asynchronous operations, use async/await syntax instead of returning Promises directly.

## Examples

Example of **incorrect** code:
```javascript
test("async operation", () => {
  return expect(fetchData()).resolves.toBe(true);
});

it("promise test", () => {
  return somePromise().then(result => {
    expect(result).toBe("value");
  });
});
```

Example of **correct** code:
```javascript
test("async operation", async () => {
  await expect(fetchData()).resolves.toBe(true);
});

it("promise test", async () => {
  const result = await somePromise();
  expect(result).toBe("value");
});
```