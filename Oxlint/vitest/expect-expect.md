Pattern: Missing assertion

Issue: -

## Description

People may forget to add assertions.

## Examples

Example of **incorrect** code:
```javascript
it("should be a test", () => {
  console.log("no assertion");
});
test("should assert something", () => {});
```
