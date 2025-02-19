Pattern: Duplicate test title

Issue: -

## Description

Using identical titles for different tests or test suites at the same level creates confusion when tests fail and makes it harder to identify which test needs fixing.

## Examples

Example of **incorrect** code:
```javascript
describe("suite", () => {
  it("should work", () => {
    expect(a).toBe(true);
  });
  
  it("should work", () => {
    expect(b).toBe(true);
  });
});

describe("feature", () => {});
describe("feature", () => {});
```

Example of **correct** code:
```javascript
describe("suite", () => {
  it("should work with A", () => {
    expect(a).toBe(true);
  });
  
  it("should work with B", () => {
    expect(b).toBe(true);
  });
});

describe("feature A", () => {});
describe("feature B", () => {});
```