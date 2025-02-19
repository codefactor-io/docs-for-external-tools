Pattern: Unordered hooks

Issue: -

## Description

Jest executes hooks in a specific order: beforeAll, beforeEach, afterEach, afterAll. Grouping hooks in this order makes the test setup and teardown flow clearer and matches the actual execution order.

## Examples

Example of **incorrect** code:
```javascript
describe("suite", () => {
  beforeEach(() => {
    setup();
  });
  beforeAll(() => {
    init();
  });
  afterEach(() => {
    cleanup();
  });
  afterAll(() => {
    teardown();
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
  afterEach(() => {
    cleanup();
  });
  afterAll(() => {
    teardown();
  });
});
```