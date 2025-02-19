Pattern: Untyped mock factory

Issue: -

## Description

Using mock factories without type parameters makes it harder to catch type-related issues when the source module changes. Mock factories should specify return types to ensure type safety.

## Examples

Example of **incorrect** code:
```typescript
jest.mock("../module", () => {
  return jest.fn(() => 42);
});

jest.mock("./service", () => ({
  handler: jest.fn(),
}));
```

Example of **correct** code:
```typescript
jest.mock<typeof import("../module")>("../module", () => {
  return jest.fn(() => 42);
});

jest.mock<typeof import("./service")>("./service", () => ({
  handler: jest.fn(),
}));
```