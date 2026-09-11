Pattern: Missing type annotation at module boundary

Issue: -

## Description

Explicit types for function return values and arguments makes it clear
to any calling code what is the module boundary's input and output.
Adding explicit type annotations for those types can help improve code
readability. It can also improve TypeScript type checking performance on
larger codebases.

## Examples

Example of **incorrect** code:
```ts
// Should indicate that no value is returned (void)
export function test() {
  return;
}

// Should indicate that a string is returned
export var arrowFn = () => "test";

// All arguments should be typed
export var arrowFn = (arg): string => `test ${arg}`;
export var arrowFn = (arg: any): string => `test ${arg}`;

export class Test {
  // Should indicate that no value is returned (void)
  method() {
    return;
  }
}
```

Example of **correct** code:
```ts
// A function with no return value (void)
export function test(): void {
  return;
}

// A return value of type string
export var arrowFn = (): string => "test";

// All arguments should be typed
export var arrowFn = (arg: string): string => `test ${arg}`;
export var arrowFn = (arg: unknown): string => `test ${arg}`;

export class Test {
  // A class method with no return value (void)
  method(): void {
    return;
  }
}

// The function does not apply because it is not an exported function.
function test() {
  return;
}
```
