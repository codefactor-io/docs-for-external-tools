Pattern: Bitwise operation for number truncation

Issue: -

## Description

Using `Math.trunc()` provides a clearer and more reliable way to truncate numbers than bitwise operations (`x | 0`, `~~x`, `x >> 0`, `x << 0`, `x ^ 0`). Bitwise operations can be unclear and fail in certain edge cases.

## Examples

Example of **incorrect** code:
```javascript
const foo = 1.1 | 0;
```

Example of **correct** code:
```javascript
const foo = Math.trunc(1.1);
```