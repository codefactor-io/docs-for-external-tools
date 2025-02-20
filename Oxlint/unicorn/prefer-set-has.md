Pattern: `Array#includes()` for repeated lookups

Issue: -

## Description

When performing frequent existence checks, using `Set#has()` is more performant than `Array#includes()`. If an array is primarily used for lookup operations, consider converting it to a `Set`.

## Examples

Example of **incorrect** code:
```js
const array = [1, 2, 3];
const hasValue = (value) => array.includes(value);
```

Example of **correct** code:
```js
const set = new Set([1, 2, 3]);
const hasValue = (value) => set.has(value);

// Single lookup is fine with array
const array = [1, 2, 3];
const hasOne = array.includes(1);
```