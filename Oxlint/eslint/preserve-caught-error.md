Pattern: Caught error not preserved

Issue: -

## Description

Re-throwing an error without preserving the original error loses important debugging information and makes it harder to trace the root cause of issues.

## Examples

Example of **incorrect** code:

```ts
try {
  doSomething();
} catch (err) {
  throw new Error("Something failed");
}
```

Example of **correct** code:

```ts
try {
  doSomething();
} catch (err) {
  throw new Error("Something failed", { cause: err });
}
```