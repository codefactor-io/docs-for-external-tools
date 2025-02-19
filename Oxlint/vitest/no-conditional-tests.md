Pattern: Conditional test declarations

Issue: -

## Description

Using conditional statements (like `if` blocks) around test cases makes tests unpredictable and harder to understand. Tests should be deterministic and straightforward to ensure reliable results and easier maintenance.

## Examples

Example of **incorrect** code:
```js
describe("my tests", () => {
  if (true) {
    it("is awesome", () => {
      doTheThing();
    });
  }
});
```

Example of **correct** code:
```js
describe("my tests", () => {
  it("is awesome", () => {
    doTheThing();
  });
});
```