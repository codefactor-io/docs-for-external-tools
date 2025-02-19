Pattern: Use of `Math.pow`

Issue: -

## Description

The `Math.pow()` function can be replaced with the more readable exponentiation operator (`**`) introduced in ES2016. Using infix notation makes the code's intent clearer than function call syntax.

## Examples

Example of **incorrect** code:
```javascript
let square = Math.pow(x, 2);
const area = Math.pow(width, 2) + Math.pow(height, 2);
let volume = Math.pow(size, 3);

const binary = Math.pow(2, 8);
let exp = Math.pow(x, y);
```

Example of **correct** code:
```javascript
let square = x ** 2;
const area = width ** 2 + height ** 2;
let volume = size ** 3;

const binary = 2 ** 8;
let exp = x ** y;

// Math.pow is ok when used with methods
Math.pow(Math.sin(x), 2);
```