Pattern: Missing message in `Error` constructor

Issue: -

## Description

Creating `Error` objects without a message parameter reduces code readability and makes debugging more difficult. Always include a descriptive error message when throwing errors.

## Examples

Example of **incorrect** code:
```javascript
throw Error();
throw new TypeError();
```

Example of **correct** code:
```javascript
throw new Error("Unexpected token");
throw new TypeError("Number expected");
```