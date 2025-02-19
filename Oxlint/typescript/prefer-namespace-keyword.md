Pattern: Use of `module` keyword instead of `namespace`

Issue: -

## Description

For internal code organization, the `namespace` keyword is preferred over the older `module` keyword. Note that using `declare module` for external API descriptions is still valid.

## Examples

Example of **incorrect** code:
```typescript
module Example {
  export function foo() {}
}
```

Example of **correct** code:
```typescript
namespace Example {
  export function foo() {}
}

// External module declaration is still valid
declare module 'external-lib' {
  export function bar(): void;
}
```