Pattern: Conditional logic inside test

Issue: -

## Description

Conditional statements in tests can make the test harder to read and understand.
It is better to have a single test case per test function.

## Examples

Example of **incorrect** code:
```javascript
it("foo", () => {
  if (true) {
    doTheThing();
  }
});

it("bar", () => {
  switch (mode) {
    case "none":
      generateNone();
    case "single":
      generateOne();
    case "multiple":
      generateMany();
  }

  expect(fixtures.length).toBeGreaterThan(-1);
});

it("baz", async () => {
  const promiseValue = () => {
    return something instanceof Promise ? something : Promise.resolve(something);
  };

  await expect(promiseValue()).resolves.toBe(1);
});
```

Example of **correct** code:
```javascript
describe("my tests", () => {
  if (true) {
    it("foo", () => {
      doTheThing();
    });
  }
});

beforeEach(() => {
  switch (mode) {
    case "none":
      generateNone();
    case "single":
      generateOne();
    case "multiple":
      generateMany();
  }
});

it("bar", () => {
  expect(fixtures.length).toBeGreaterThan(-1);
});

const promiseValue = (something) => {
  return something instanceof Promise ? something : Promise.resolve(something);
};

it("baz", async () => {
  await expect(promiseValue()).resolves.toBe(1);
});
```
