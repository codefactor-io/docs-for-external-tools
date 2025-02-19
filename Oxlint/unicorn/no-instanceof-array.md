Pattern: `instanceof Array` check

Issue: -

## Description

Using `instanceof Array` to check for arrays doesn't work reliably across different contexts (e.g., frames/windows in browsers or VM modules in Node.js). Use `Array.isArray()` instead.

## Examples

Example of **incorrect** code:
```javascript
array instanceof Array;
[1, 2, 3] instanceof Array;
```

Example of **correct** code:
```javascript
Array.isArray(array);
Array.isArray([1, 2, 3]);
```