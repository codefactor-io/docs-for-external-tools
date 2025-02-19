Pattern: Use of Jasmine global

Issue: -

## Description

Using Jasmine globals in Jest tests is deprecated. Jest provides its own equivalent APIs that should be used instead of legacy Jasmine functions and properties.

## Examples

Example of **incorrect** code:
```javascript
jasmine.DEFAULT_TIMEOUT_INTERVAL = 5000;
test("spy test", () => {
  const spy = jasmine.createSpy();
  pending();
});
```

Example of **correct** code:
```javascript
jest.setTimeout(5000);
test("spy test", () => {
  const spy = jest.fn();
  test.skip();
});
```