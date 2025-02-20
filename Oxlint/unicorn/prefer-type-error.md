Pattern: Generic `Error` after type check

Issue: -

## Description

When throwing an error after a type check, using `TypeError` is more appropriate than a generic `Error` as it specifically indicates that the error is related to an unexpected type, making debugging easier.

## Examples

Example of **incorrect** code:
```javascript
if (Array.isArray(foo)) {
  throw new Error("Expected foo to be an array");
}
```

Example of **correct** code:
```javascript
if (Array.isArray(foo)) {
  throw new TypeError("Expected foo to be an array");
}
```