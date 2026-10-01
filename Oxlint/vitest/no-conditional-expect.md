Pattern: Conditional assertion

Issue: -

## Description

Jest only considers a test to have failed if it throws an error, meaning if calls to
assertion functions like `expect` occur in conditional code such as a `catch` statement,
tests can end up passing but not actually test anything. Additionally, conditionals
tend to make tests more brittle and complex, as they increase the amount of mental
thinking needed to understand what is actually being tested.

## Examples

Example of **incorrect** code:
```javascript
it("foo", () => {
  doTest && expect(1).toBe(2);
});

it("bar", () => {
  if (!skipTest) {
    expect(1).toEqual(2);
  }
});

it("baz", async () => {
  try {
    await foo();
  } catch (err) {
    expect(err).toMatchObject({ code: "MODULE_NOT_FOUND" });
  }
});

it("throws an error", async () => {
  await foo().catch((error) => expect(error).toBeInstanceOf(error));
});
```

Example of **correct** code:
```javascript
it("foo", () => {
  expect(!value).toBe(false);
});

function getValue() {
  if (process.env.FAIL) {
    return 1;
  }
  return 2;
}

it("foo", () => {
  expect(getValue()).toBe(2);
});

it("validates the request", () => {
  try {
    processRequest(request);
  } catch {
  } finally {
    expect(validRequest).toHaveBeenCalledWith(request);
  }
});

it("throws an error", async () => {
  await expect(foo).rejects.toThrow(Error);
});
```
