Pattern: Missing vitest global import

Issue: -

## Description

Using vitest globals without importing them relies on implicit global configuration (`globals: true` in vitest config). Explicit imports make dependencies clear, improve IDE support, and ensure compatibility across different setups.

## Examples

Example of **incorrect** code:

```ts
describe("suite", () => {
  it("test", () => {
    expect(true).toBe(true);
  });
});
```

Example of **correct** code:

```ts
import { describe, it, expect } from "vitest";

describe("suite", () => {
  it("test", () => {
    expect(true).toBe(true);
  });
});
```