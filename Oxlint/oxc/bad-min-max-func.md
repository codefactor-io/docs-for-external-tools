Pattern: Invalid min/max clamp

Issue: -

## Description

When using Math.min and Math.max for clamping values, the arguments must be in the correct order. Incorrect ordering can result in the function always returning the same constant value.

## Examples

Example of **incorrect** code:
```javascript
const value = Math.min(Math.max(100, x), 0);
const num = Math.max(1000, Math.min(0, x));
```

Example of **correct** code:
```javascript
const value = Math.min(Math.max(0, x), 100);
const num = Math.max(0, Math.min(1000, x));
```