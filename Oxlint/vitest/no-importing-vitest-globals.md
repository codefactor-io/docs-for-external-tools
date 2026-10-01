Pattern: Import of Vitest globals

Issue: -

## Description

If a project is [configured to provide Vitest functions as globals](https://vitest.dev/config/globals.html),
this rule can be used to ensure that the globals are never imported
via `import` or `require`.

Note that this rule should *not* be used if the `globals` config
option is set to `false` in Vitest (`false` is the default configuration).

## Examples

Example of **incorrect** code:
```javascript
import { test, expect } from "vitest";

test("foo", () => {
  expect(1).toBe(1);
});

const { test, expect } = require("vitest");

test("foo", () => {
  expect(1).toBe(1);
});
```

Example of **correct** code:
```javascript
test("foo", () => {
  expect(1).toBe(1);
});
```
