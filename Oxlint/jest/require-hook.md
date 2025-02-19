Pattern: Missing test hook

Issue: -

## Description

Test setup and cleanup should be contained within Jest hooks (beforeAll, beforeEach, afterEach, afterAll) rather than being executed directly in the test file or describe block.

## Examples

Example of **incorrect** code:
```javascript
const setup = () => {
  database.connect();
};

setup(); // Direct call outside hook

describe("tests", () => {
  mockFunction(); // Direct mock setup
  
  test("example", () => {
    expect(database.isConnected()).toBe(true);
  });
});
```

Example of **correct** code:
```javascript
const setup = () => {
  database.connect();
};

beforeAll(() => {
  setup();
});

describe("tests", () => {
  beforeEach(() => {
    mockFunction();
  });
  
  test("example", () => {
    expect(database.isConnected()).toBe(true);
  });
});
```