Pattern: Error assertion without expected message

Issue: -

## Description

Using `toThrow()` or `toThrowError()` without specifying an expected error message
makes tests less specific and harder to debug. When a test only checks that an
error was thrown but not what kind of error, it can pass even when the wrong
error is thrown, potentially hiding bugs. Providing an expected error message
or error type makes tests more precise and helps catch regressions more effectively.

## Examples

Example of **incorrect** code:
```javascript
test("all the things", async () => {
  expect(() => a()).toThrow();
  expect(() => a()).toThrowError();
  await expect(a()).rejects.toThrow();
  await expect(a()).rejects.toThrowError();
});
```

Example of **correct** code:
```javascript
test("all the things", async () => {
  expect(() => a()).toThrow("a");
  expect(() => a()).toThrowError("a");
  await expect(a()).rejects.toThrow("a");
  await expect(a()).rejects.toThrowError("a");
});
```
