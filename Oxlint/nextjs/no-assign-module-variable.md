Pattern: Module variable assignment

Issue: -

## Description

Assigning to the module variable in Next.js can cause unexpected behavior and break hot module replacement. Use exports or state management instead of modifying the module object directly.

## Examples

Example of **incorrect** code:
```javascript
module.value = "something";
module.exports.foo = "bar";
```

Example of **correct** code:
```javascript
export const value = "something";
export const foo = "bar";
```