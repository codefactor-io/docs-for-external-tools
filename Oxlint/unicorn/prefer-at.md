Pattern: Length-based or legacy index access

Issue: -

## Description

The `.at()` method is more readable and consistent for accessing elements by index,
especially for negative indices which access elements from the end of the array or string.

## Examples

Example of **incorrect** code:
```javascript
const foo = array[array.length - 1];
const foo = array.slice(-1)[0];
const foo = string.charAt(string.length - 1);
```

Example of **correct** code:
```javascript
const foo = array.at(-1);
const foo = array.at(-5);
const foo = string.at(-1);
```
