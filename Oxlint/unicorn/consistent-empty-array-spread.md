Pattern: Inconsistent empty array spread in ternary

Issue: -

## Description

When spreading a ternary expression in an array, use consistent types (either arrays or strings) in both branches for better code clarity.

## Examples

Example of **incorrect** code:
```javascript
const array = [a, ...(foo ? [b, c] : "")];
const array = [a, ...(foo ? "bc" : [])];
```

Example of **correct** code:
```javascript
const array = [a, ...(foo ? [b, c] : [])];
const array = [a, ...(foo ? "bc" : "")];
```