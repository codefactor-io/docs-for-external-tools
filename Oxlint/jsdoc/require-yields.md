Pattern: Missing yield documentation

Issue: -

## Description

Generator functions that yield values must document those values with a @yields tag. Multiple @yields tags on the same function are not allowed.

## Examples

Example of **incorrect** code:
```javascript
function* getData() {
  yield "first";
  yield "second";
}

/**
 * @yields {string} First value
 * @yields {string} Second value
 */
function* getValues() {
  yield "value";
}
```

Example of **correct** code:
```javascript
/**
 * @yields {string} Sequential string values
 */
function* getData() {
  yield "first";
  yield "second";
}
```