Pattern: Misplaced hook

Issue: -

## Description

While hooks can be placed anywhere in a test file, they are always executed in a specific order. Placing hooks between test cases makes the code flow harder to understand and can lead to confusion about execution order.

## Examples

Example of **incorrect** code:
```javascript
describe("suite", () => {
  it("test one", () => {});
  
  beforeEach(() => {
    setup();
  });
  
  it("test two", () => {});
  
  beforeAll(() => {
    init();
  });
});
```

Example of **correct** code:
```javascript
describe("suite", () => {
  beforeAll(() => {
    init();
  });
  
  beforeEach(() => {
    setup();
  });

  it("test one", () => {});
  it("test two", () => {});
});
```