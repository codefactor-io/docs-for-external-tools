Pattern: Use of `new Array()` constructor

Issue: -

## Description

The `Array` constructor with a single argument is ambiguous - it's unclear whether the argument specifies the array length or is meant to be the only element. Use `Array.from()` for length initialization or array literals for single elements.

## Examples

Example of **incorrect** code:
```javascript
const array = new Array(1);
const array = new Array(42);
const array = new Array(foo);
```

Example of **correct** code:
```javascript
const array = Array.from({ length: 42 });
const array = [42];
```