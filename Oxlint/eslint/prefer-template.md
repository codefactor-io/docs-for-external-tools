Pattern: String concatenation instead of template literal

Issue: -

## Description

In ES2015 (ES6), we can use template literals instead of string concatenation.

## Examples

Example of **incorrect** code:
```javascript
const str = "Hello, " + name + "!";
const str1 = "Time: " + 12 * 60 * 60 * 1000;
```

Example of **correct** code:
```javascript
const str = "Hello World!";
const str2 = `Time: ${12 * 60 * 60 * 1000}`;
const str4 = "Hello, " + "World!";
```
