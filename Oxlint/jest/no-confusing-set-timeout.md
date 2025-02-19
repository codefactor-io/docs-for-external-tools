Pattern: Misplaced setTimeout call

Issue: -

## Description

Calling `jest.setTimeout()` anywhere other than in global scope can lead to confusing behavior. The timeout should not be called multiple times or after Jest functions like hooks, describe, or test.

## Examples

Example of **incorrect** code:
```javascript
describe("test suite", () => {
  jest.setTimeout(1000);
  
  it("test case", () => {
    // test logic
  });
});

test("foo", () => {
  jest.setTimeout(1000);
});

beforeEach(() => {
  jest.setTimeout(1000);
});
```

Example of **correct** code:
```javascript
jest.setTimeout(1000);

describe("test suite", () => {
  it("test case", () => {
    // test logic
  });
});
```