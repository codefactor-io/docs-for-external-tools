Pattern: Redundant assignment operation

Issue: -

## Description

Using patterns like `a += a + b` or `a -= a - b` is likely a mistake. These expressions can be simplified to `a += b` or `a -= b` respectively, as the original variable is being added or subtracted unnecessarily.

## Examples

Example of **incorrect** code:
```javascript
x += x + y;
count -= count - total;
sum *= sum * factor;
```

Example of **correct** code:
```javascript
x += y;
count -= total;
sum *= factor;
```