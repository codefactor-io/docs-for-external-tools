Pattern: Use of test hook

Issue: -

## Description

Using Jest setup and teardown hooks (beforeAll, beforeEach, afterAll, afterEach) promotes shared state between tests, making them harder to understand and maintain in isolation.

## Examples

Example of **incorrect** code:
```javascript
describe("suite", () => {
  let data;
  beforeEach(() => {
    data = setupData();
  });
  afterEach(() => {
    data = null;
  });
  
  test("case", () => {
    expect(data.value).toBe(true);
  });
});
```

Example of **correct** code:
```javascript
describe("suite", () => {
  test("case", () => {
    const data = setupData();
    expect(data.value).toBe(true);
  });
});
```