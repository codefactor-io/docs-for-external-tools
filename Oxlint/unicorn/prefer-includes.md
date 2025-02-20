Pattern: Use of `indexOf()` for existence check

Issue: -

## Description

The `includes()` method provides a more readable and less error-prone way to check for element existence compared to using `indexOf() !== -1` checks. All built-in types that have `indexOf()` also support `includes()`.

## Examples

Example of **incorrect** code:
```javascript
if (str.indexOf("foo") !== -1) {
}
```

Example of **correct** code:
```javascript
if (str.includes("foo")) {
}
```