Pattern: Conditional logic in test

Issue: -

## Description

Using conditional statements in tests makes them harder to understand and maintain. Each test should verify a single, specific case without branching logic.

## Examples

Example of **incorrect** code:
```javascript
it("test", () => {
  if (mode === "dev") {
    expect(value).toBe(1);
  } else {
    expect(value).toBe(2);
  }
});

it("test", () => {
  switch(type) {
    case "A": verifyA();
    case "B": verifyB();
  }
});
```

Example of **correct** code:
```javascript
it("test in dev mode", () => {
  setMode("dev");
  expect(value).toBe(1);
});

it("test in prod mode", () => {
  setMode("prod");
  expect(value).toBe(2);
});

it("verifies type A", () => {
  verifyA();
});

it("verifies type B", () => {
  verifyB();
});
```