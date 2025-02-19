Pattern: Invalid test title

Issue: -

## Description

Test block titles must be non-empty strings without leading/trailing spaces and should not be prefixed with their block name. Invalid titles make test output harder to understand.

## Examples

Example of **incorrect** code:
```javascript
describe("", () => {});
it(" has spaces ", () => {});
test("test: should work", () => {});
describe("describe: my suite", () => {});
```

Example of **correct** code:
```javascript
describe("feature", () => {});
it("should handle edge case", () => {});
test("returns correct value", () => {});
```