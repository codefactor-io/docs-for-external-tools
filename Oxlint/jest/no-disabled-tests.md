Pattern: Disabled test

Issue: -

## Description

Using `.skip`, `x` prefix, or empty test functions to disable tests can be useful during development, but disabled tests should be either removed or enabled before committing changes.

## Examples

Example of **incorrect** code:
```javascript
describe.skip("suite", () => {});
xdescribe("suite", () => {});
it.skip("test", () => {});
xit("test", () => {});
test("empty"); // Empty test
```

Example of **correct** code:
```javascript
describe("suite", () => {
  test("case", () => {
    expect(value).toBe(true);
  });
});

it("test", () => {
  expect(result).toBe(false);
});
```