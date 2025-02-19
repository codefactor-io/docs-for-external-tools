Pattern: Legacy array flattening technique

Issue: -

## Description

ES2019's `Array#flat()` method provides a cleaner way to flatten arrays compared to older techniques like `reduce()`, `concat()`, or spread operators.

## Examples

Example of **incorrect** code:
```javascript
const foo = array.reduce((a, b) => a.concat(b), []);
const foo = array.reduce((a, b) => [...a, ...b], []);
const foo = [].concat(...array);
const foo = [].concat.apply([], array);
const foo = Array.prototype.concat.apply([], array);
```

Example of **correct** code:
```javascript
const foo = array.flat();
const foo = [maybeArray].flat();
```