Pattern: Use of reference value in `Array#fill()`

Issue: -

## Description

`Array#fill()` reuses the same value for every array element. When the
fill value is an object, array, class, or most constructed objects, all
elements point at the same reference and mutating one element mutates the
shared value observed by the others.

## Examples

Example of **incorrect** code:
```javascript
const rows = new Array(3).fill({});
rows[0].selected = true; // Every row now has `selected`.
```

Example of **correct** code:
```javascript
const rows = Array.from({ length: 3 }, () => ({}));
```
