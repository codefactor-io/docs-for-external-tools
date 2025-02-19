Pattern: Expect outside test block

Issue: -

## Description

Using expect statements outside of test blocks (it or test) prevents proper test execution and reporting. Helper functions containing expect statements are allowed.

## Examples

Example of **incorrect** code:
```javascript
describe("suite", () => {
  expect(value).toBe(true);
});

expect(result).toEqual(expected);
```

Example of **correct** code:
```javascript
describe("suite", () => {
  it("test case", () => {
    expect(value).toBe(true);
  });
});

const checkValue = () => {
  expect(value).toBe(true);
};
```