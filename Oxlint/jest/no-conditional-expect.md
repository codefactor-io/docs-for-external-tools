Pattern: Conditional assertion

Issue: -

## Description

Using expect in conditional blocks (if statements, catch blocks, or conditional callbacks) can result in tests that pass without actually testing anything, since Jest only fails a test when an error is thrown.

## Examples

Example of **incorrect** code:
```javascript
it("test", () => {
  if (condition) {
    expect(value).toBe(true);
  }
});

it("error", async () => {
  try {
    await operation();
  } catch (err) {
    expect(err.code).toBe("ERROR");
  }
});
```

Example of **correct** code:
```javascript
it("test", () => {
  expect(condition).toBe(true);
  expect(value).toBe(true);
});

it("error", async () => {
  await expect(operation).rejects.toThrow("ERROR");
});
```