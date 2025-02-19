Pattern: Use of TypeScript namespace syntax

Issue: -

## Description

TypeScript namespaces (`namespace` and `module` declarations) are an outdated way to organize code. Use ES2015 module syntax (`import`/`export`) instead for better compatibility and tooling support.

## Examples

Example of **incorrect** code:
```typescript
module foo {
  export function bar() {}
}

namespace baz {
  export interface Qux {}
}
```

Example of **correct** code:
```typescript
export function bar() {}
export interface Qux {}
```