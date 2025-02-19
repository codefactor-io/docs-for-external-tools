Pattern: Export in test file

Issue: -

## Description

Exporting from test files causes tests to run multiple times when the export is imported elsewhere. Helper functions should be moved to separate utility files instead of being exported from test files.

## Examples

Example of **incorrect** code:
```javascript
export const helper = () => {
  return "test value";
};

describe("suite", () => {
  test("case", () => {
    expect(helper()).toBe("test value");
  });
});
```

Example of **correct** code:
```javascript
// test-helpers.js
export const helper = () => {
  return "test value";
};

// test.test.js
import { helper } from "./test-helpers";

describe("suite", () => {
  test("case", () => {
    expect(helper()).toBe("test value");
  });
});
```