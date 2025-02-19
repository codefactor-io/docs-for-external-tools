Pattern: Manual test loop

Issue: -

## Description

Using manual loops for test cases is less readable and more error-prone than using Jest's built-in `each` functionality, which provides a clearer way to handle parameterized tests.

## Examples

Example of **incorrect** code:
```javascript
for (const item of items) {
  it("should process item", () => {
    expect(process(item)).toBe("result");
  });
}
```

Example of **correct** code:
```javascript
it.each(items)("should process item", (item) => {
  expect(process(item)).toBe("result");
});
```