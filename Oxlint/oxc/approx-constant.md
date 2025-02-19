Pattern: Approximate mathematical constant

Issue: -

## Description

Using approximate values for mathematical constants is less precise than using the built-in Math constants. The Math object provides exact values for common mathematical constants.

## Examples

Example of **incorrect** code:
```javascript
const pi = 3.14159;
const e = 2.718;
const log2e = 1.443;
```

Example of **correct** code:
```javascript
const pi = Math.PI;
const e = Math.E;
const log2e = Math.LOG2E;
```