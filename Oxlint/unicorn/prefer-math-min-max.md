Pattern: Ternary expression for min/max comparison

Issue: -

## Description

Using `Math.min()` and `Math.max()` functions provides a more concise and clearer way to handle value boundaries compared to ternary expressions, making the code easier to understand and less prone to errors.

## Examples

Example of **incorrect** code:
```javascript
height > 50 ? 50 : height;
height > 50 ? height : 50;
```

Example of **correct** code:
```javascript
Math.min(height, 50);
Math.max(height, 50);
```