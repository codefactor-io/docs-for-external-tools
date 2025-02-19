Pattern: Extra space in `console` method arguments

Issue: -

## Description

Console methods automatically add spaces between arguments when joining them. Adding leading or trailing spaces in the arguments results in double spaces in the output.

## Examples

Example of **incorrect** code:
```javascript
console.log("abc ", "def");
console.log(" abc", "def");
console.log("abc", " def");
```

Example of **correct** code:
```javascript
console.log("abc", "def");
```