Pattern: Use of `eval` function

Issue: -

## Description

The `eval` function executes arbitrary JavaScript code as a string, which can lead to security vulnerabilities and make code harder to analyze. It's also not supported in secure contexts and can have significant performance implications.

## Examples

Example of **incorrect** code:
```javascript
eval("console.log('Hello')");

const expression = "2 + 2";
eval(expression);

window.eval("alert('warning')");
```

Example of **correct** code:
```javascript
console.log('Hello');

const result = 2 + 2;

// For dynamic property access
const obj = { key: 'value' };
const key = 'key';
const value = obj[key];
```