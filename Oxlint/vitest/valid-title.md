Pattern: Invalid test title

Issue: -

## Description

Titles that are not valid can be misleading and make it harder to understand the purpose of the test.

## Examples

Example of **incorrect** code:
```javascript
describe("", () => {});
describe("foo", () => {
  it("", () => {});
});
it("", () => {});
test("", () => {});
xdescribe("", () => {});
xit("", () => {});
xtest("", () => {});
```

Example of **correct** code:
```javascript
describe("foo", () => {});
it("bar", () => {});
test("baz", () => {});
```
