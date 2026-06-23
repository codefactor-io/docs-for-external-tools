Pattern: Ungrouped exports

Issue: -

## Description

An export declaration or `module.exports` assignment can appear anywhere in the code.
By requiring a single export declaration all your exports will remain at one place,
making it easier to see what exports a module provides.

## Examples

Example of **incorrect** code:
```javascript
export const first = true;
export const second = true;
```

Example of **correct** code:
```javascript
const first = true;
const second = true;
export { first, second };
```
