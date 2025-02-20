Pattern: Legacy mathematical operation patterns

Issue: -

## Description

Modern JavaScript provides more concise and readable alternatives to legacy mathematical operations. For example, `Math.log10(x)` should be used instead of `Math.log(x) * Math.LOG10E`, and `Math.hypot(a, b)` is preferred over `Math.sqrt(a * a + b * b)`.

## Examples

Example of **incorrect** code:
```javascript
Math.log(x) * Math.LOG10E;
Math.sqrt(a * a + b * b);
```

Example of **correct** code:
```javascript
Math.log10(x);
Math.hypot(a, b);
```