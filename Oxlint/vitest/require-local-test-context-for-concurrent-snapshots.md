Pattern: Missing test context in concurrent snapshot tests

Issue: -

## Description

Running snapshot tests concurrently without proper test context can lead to unreliable or inconsistent results. Using local test context (`{ expect }` or `context`) ensures snapshots remain accurate and stable when running tests in parallel.

## Examples

Example of **incorrect** code:
```javascript
test.concurrent("myLogic", () => {
  expect(true).toMatchSnapshot();
});

describe.concurrent("something", () => {
  test("myLogic", () => {
    expect(true).toMatchInlineSnapshot();
  });
});
```

Example of **correct** code:
```javascript
test.concurrent("myLogic", ({ expect }) => {
  expect(true).toMatchSnapshot();
});

test.concurrent("myLogic", (context) => {
  context.expect(true).toMatchSnapshot();
});
```