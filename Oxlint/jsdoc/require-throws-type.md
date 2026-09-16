Pattern: Untyped `@throws` tag

Issue: -

## Description

A `@throws` tag should document the type of error that may be thrown.

## Examples

Example of **incorrect** code:
```javascript
/** @throws */
function quux() {
  throw new Error("error");
}
```

Example of **correct** code:
```javascript
/** @throws {Error} */
function quux() {
  throw new Error("error");
}
```
