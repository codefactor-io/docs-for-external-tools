Pattern: Import of `node:test` instead of `vitest`

Issue: -

## Description

Importing from `node:test` instead of `vitest` can lead to inconsistent test results and missing features. Using `vitest` ensures compatibility and access to all testing functionality.

## Examples

Example of **incorrect** code:
```javascript
import { test } from "node:test";
import { expect } from "vitest";

test("foo", () => {
  expect(1).toBe(1);
});
```

Example of **correct** code:
```javascript
import { test, expect } from "vitest";

test("foo", () => {
  expect(1).toBe(1);
});
```