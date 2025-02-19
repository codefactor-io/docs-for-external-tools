Pattern: Duplicate hook

Issue: -

## Description

Using multiple instances of the same hook (beforeEach, afterEach, etc.) within a describe block creates confusion and may lead to unexpected behavior. Each hook type should only be used once per scope.

## Examples

Example of **incorrect** code:
```javascript
describe("suite", () => {
  beforeEach(() => {
    setup1();
  });
  beforeEach(() => {
    setup2();
  });
  
  test("foo", () => {
    expect(value).toBe(true);
  });
});
```

Example of **correct** code:
```javascript
describe("suite", () => {
  beforeEach(() => {
    setup1();
    setup2();
  });
  
  test("foo", () => {
    expect(value).toBe(true);
  });
});
```