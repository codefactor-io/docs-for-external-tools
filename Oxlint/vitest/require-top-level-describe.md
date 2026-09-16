Pattern: Test or hook outside top-level `describe`

Issue: -

## Description

Having tests and hooks organized within `describe` blocks provides better
structure and grouping for test suites. It makes test output more readable
and helps with test organization, especially in larger codebases.

This rule triggers a warning if a test case (`test` and `it`) or a hook
(`beforeAll`, `beforeEach`, `afterEach`, `afterAll`) is not located in a
top-level `describe` block.

## Examples

Example of **incorrect** code:
```javascript
// Above a describe block
test("my test", () => {});
describe("test suite", () => {
  it("test", () => {});
});

// Below a describe block
describe("test suite", () => {});
test("my test", () => {});

// Same for hooks
beforeAll("my beforeAll", () => {});
describe("test suite", () => {});
afterEach("my afterEach", () => {});
```

Example of **correct** code:
```javascript
// Above a describe block
// In a describe block
describe("test suite", () => {
  test("my test", () => {});
});

// In a nested describe block
describe("test suite", () => {
  test("my test", () => {});
  describe("another test suite", () => {
    test("my other test", () => {});
  });
});
```
