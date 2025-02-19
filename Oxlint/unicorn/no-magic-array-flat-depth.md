Pattern: Unexplained depth in `Array#flat()`

Issue: -

## Description

Using magic numbers for the `Array#flat()` depth parameter makes code harder to understand. Common values are `1` (default) and `Infinity`. When using other values, add a comment explaining the depth.

## Examples

Example of **incorrect** code:
```javascript
array.flat(2);
array.flat(20);
```

Example of **correct** code:
```javascript
array.flat(2 /* for nested arrays of json responses */);
array.flat(1);
array.flat();
array.flat(Infinity);
```