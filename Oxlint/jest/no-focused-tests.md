Pattern: Focused test

Issue: -

## Description

Using `.only` or the `f` prefix to focus tests is helpful for debugging, but these focused tests should be removed before committing changes to ensure all tests are executed in the test suite.

## Examples

Example of **incorrect** code:
```javascript
describe.only("suite", () => {
  test("case", () => {});
});

it.only("test", () => {});
fit("test", () => {});
test.only("case", () => {});
```

Example of **correct** code:
```javascript
describe("suite", () => {
  test("case", () => {});
});

it("test", () => {});
test("case", () => {});
```