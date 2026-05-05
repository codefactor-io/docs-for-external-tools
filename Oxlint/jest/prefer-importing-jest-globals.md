Pattern: Missing Jest global import

Issue: -

## Description

Using global Jest functions without explicit imports makes dependencies implicit and can cause issues with type checking, editor tooling, and when migrating between test runners.

## Examples

Example of **incorrect** code:

```ts
describe("suite", () => {
  test("foo");
  expect(true).toBeDefined();
});
```

Example of **correct** code:

```ts
import { describe, expect, test } from "@jest/globals";
describe("suite", () => {
  test("foo");
  expect(true).toBeDefined();
});
```