Pattern: Manual loops in test cases

Issue: -

## Description

Using manual loops for test cases can be error-prone and reduce code clarity. The `each` method provides a cleaner way to write parameterized tests, improving readability and maintainability.

## Examples

Example of **incorrect** code:
```js
for (const item of items) {
  describe(item, () => {
    expect(item).toBe("foo");
  });
}
```

Example of **correct** code:
```js
describe.each(items)("item", (item) => {
  expect(item).toBe("foo");
});
```