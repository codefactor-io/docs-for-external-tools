Pattern: Await in expect

Issue: -

## Description

Using `await` inside `expect()` makes promise rejection errors harder to debug than using the `.resolves` matcher. The `.resolves` syntax also provides better consistency with the `.rejects` matcher for testing promise rejections.

## Examples

Example of **incorrect** code:
```javascript
it("resolves value", async () => {
  expect(await somePromise()).toBe(true);
  expect(await getData()).toEqual({ id: 1 });
});
```

Example of **correct** code:
```javascript
it("resolves value", async () => {
  await expect(somePromise()).resolves.toBe(true);
  await expect(getData()).resolves.toEqual({ id: 1 });
});
```