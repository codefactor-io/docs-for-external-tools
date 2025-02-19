Pattern: Invalid describe callback

Issue: -

## Description

The callback function passed to `describe()` must be synchronous, have no parameters, and not return any values. Using async callbacks, parameters, or return statements can lead to unexpected test behavior.

## Examples

Example of **incorrect** code:
```javascript
describe("suite", async () => {
  test("case", () => {});
});

describe("suite", (done) => {
  test("case", () => {});
});

describe("suite", () => 
  test("case", () => {})
);
```

Example of **correct** code:
```javascript
describe("suite", () => {
  test("case", () => {});
});
```