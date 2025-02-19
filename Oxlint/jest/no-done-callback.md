Pattern: Done callback

Issue: -

## Description

Using the `done` callback for asynchronous tests is error-prone and requires careful handling of assertions. Using async/await or returning promises provides clearer and more reliable test code.

## Examples

Example of **incorrect** code:
```javascript
test("async test", (done) => {
  fetchData((data) => {
    expect(data).toBe("value");
    done();
  });
});

beforeEach((done) => {
  setupAsync(() => done());
});
```

Example of **correct** code:
```javascript
test("async test", async () => {
  const data = await fetchData();
  expect(data).toBe("value");
});

beforeEach(async () => {
  await setupAsync();
});
```