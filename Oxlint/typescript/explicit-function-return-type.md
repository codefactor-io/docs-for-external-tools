Pattern: Missing function return type annotation 

Issue: -

## Description

Explicit return type annotations make it visually clear what type a function returns and can improve TypeScript type checking performance in large codebases.

## Examples

Example of **incorrect** code:
```ts
function test() {
  return;
}

var fn = function() {
  return 1;
};

var arrowFn = () => "test";
```

Example of **correct** code:
```ts
function test(): void {
  return;
}

var fn = function(): number {
  return 1;
};

var arrowFn = (): string => "test";
```