Pattern: Invalid number method argument

Issue: -

## Description

Number methods like `toString`, `toFixed`, `toExponential`, and `toPrecision` have specific valid ranges for their arguments. Using values outside these ranges will cause errors or unexpected results.

## Examples

Example of **incorrect** code:
```javascript
number.toString(37);  // radix must be 2-36
number.toFixed(21);   // precision must be 0-20
number.toPrecision(0);  // precision must be 1-21
```

Example of **correct** code:
```javascript
number.toString(16);  // valid hexadecimal
number.toFixed(2);    // two decimal places
number.toPrecision(5);  // five significant digits 
```