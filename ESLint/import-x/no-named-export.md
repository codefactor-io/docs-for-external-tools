Pattern: Named export usage

Issue: -

## Description

This rule prohibits named exports, favoring default exports instead. It is mostly an inverse of the `no-default-export` rule. Using default exports can sometimes create a clearer API for module consumers and enforce a single responsibility principle for modules.

## Examples

Example of **incorrect** code:
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
// Re-exporting from another module
export * from './other-module'
```

```javascript
// Mixing default and named exports
export const foo = 'foo'
const bar = 'bar'
export default 'bar'
```

Example of **correct** code:
```javascript
// Single default export
export default 'bar'
```

```javascript
// Single default export using named variable
const foo = 'foo'
export { foo as default }
```

```javascript
// Re-exporting a default
export default from './other-module'
```