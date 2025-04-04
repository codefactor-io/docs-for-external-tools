Pattern: Default export usage

Issue: -

## Description

This rule prohibits default exports, favoring named exports instead. It is mostly an inverse of the `prefer-default-export` rule. Using named exports can improve code clarity by making imports more explicit and consistent throughout a codebase.

## Examples

Example of **incorrect** code:
```javascript
// Direct default export
export const foo = 'foo'
const bar = 'bar'
export default 'bar'
```

```javascript
// Default export via re-naming
const foo = 'foo'
export { foo as default }
```

Example of **correct** code:
```javascript
// Single named export
export const foo = 'foo'
```

```javascript
// Multiple named exports
export const foo = 'foo'
export const bar = 'bar'
```

```javascript
// Grouped named exports
const foo = 'foo'
const bar = 'bar'
export { foo, bar }
```

```javascript
// Batch export (remote module is not inspected)
export * from './other-module'
```