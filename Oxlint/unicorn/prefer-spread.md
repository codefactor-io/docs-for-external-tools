Pattern: Use of `Array.from()` instead of spread operator

Issue: -

## Description

The spread operator (`...`) provides a more concise and readable way to convert iterables to arrays compared to using `Array.from()`. Use spread syntax when converting simple iterables to arrays.

## Examples

Example of **incorrect** code:
```javascript
const foo = Array.from(set);
const foo = Array.from(new Set([1, 2]));
```

Example of **correct** code:
```javascript
[...set].map(() => {});
Array.from(...argumentsArray);
```