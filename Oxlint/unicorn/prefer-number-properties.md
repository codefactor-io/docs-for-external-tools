Pattern: Global number utilities usage

Issue: -

## Description

ECMAScript 2015 moved global number utilities onto the `Number` constructor for consistency. Using methods like `Number.parseInt()`, `Number.isNaN()`, and constants like `Number.POSITIVE_INFINITY` is preferred over their global counterparts. Some methods like `Number.isNaN()` and `Number.isFinite()` also provide more precise behavior than their global versions.

## Examples

Example of **incorrect** code:
```javascript
const foo = parseInt("10", 2);
const bar = parseFloat("10.5");
const check = isNaN(value);
if (value === Infinity) {}
```

Example of **correct** code:
```javascript
const foo = Number.parseInt("10", 2);
const bar = Number.parseFloat("10.5");
const check = Number.isNaN(value);
if (value === Number.POSITIVE_INFINITY) {}
```