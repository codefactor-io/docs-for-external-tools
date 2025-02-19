Pattern: Test outside describe

Issue: -

## Description

Test cases and hooks should be contained within a top-level describe block to provide better organization and context for the test suite. This makes test output more readable and maintainable.

## Examples

Example of **incorrect** code:
```javascript
beforeEach(() => {
  setup();
});

test("standalone test", () => {
  expect(value).toBe(true);
});

describe("some tests", () => {});

afterAll(() => {
  cleanup();
});
```

Example of **correct** code:
```javascript
describe("feature", () => {
  beforeEach(() => {
    setup();
  });

  test("behavior", () => {
    expect(value).toBe(true);
  });

  afterAll(() => {
    cleanup();
  });
});
```