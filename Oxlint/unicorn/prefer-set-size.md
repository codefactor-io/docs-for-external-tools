Pattern: Array conversion to get `Set` size

Issue: -

## Description

Converting a `Set` to an array just to get its length is unnecessary and less performant. The `Set` class provides a direct `size` property that should be used instead.

## Examples

Example of **incorrect** code:
```javascript
const length = [...new Set([1, 2, 3])].length;
```

Example of **correct** code:
```javascript
const size = new Set([1, 2, 3]).size;
```