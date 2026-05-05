Pattern: Test without an explicit timeout

Issue: -

## Description

Tests without an explicit timeout rely on the default, which may be too generous to catch performance regressions or too short for slow CI environments, leading to flaky failures.

## Examples

Example of **incorrect** code:

```ts
it("slow test", async () => {
  await doSomethingSlow();
});
```

Example of **correct** code:

```ts
// good (numeric timeout)
test("slow test", async () => {
  await doSomethingSlow();
}, 1000);

// good (options object)
test("slow test", { timeout: 1000 }, async () => {
  await doSomethingSlow();
});

// good (file-level)
vi.setConfig({ testTimeout: 1000 });

test("slow test", async () => {
  await doSomethingSlow();
});
```