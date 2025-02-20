Pattern: Missing digits argument in `Number#toFixed()`

Issue: -

## Description

When using `Number#toFixed()`, explicitly specifying the number of decimal places makes the code's intent clearer rather than relying on the default value of 0. This helps prevent confusion and improves code readability.

## Examples

Example of **incorrect** code:
```javascript
number.toFixed();
```

Example of **correct** code:
```javascript
number.toFixed(0);
number.toFixed(2);
```