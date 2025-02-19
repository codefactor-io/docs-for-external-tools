Pattern: Empty `Object()` constructor call

Issue: -

## Description

Using the `Object` constructor to create empty objects is discouraged in favor of object literal notation. The only valid use case for `Object()` or `new Object()` is when intentionally wrapping a value to create an object.

## Examples

Example of **incorrect** code:
```javascript
const obj = new Object();
const dict = Object();

function createObj() {
  return new Object();
}
```

Example of **correct** code:
```javascript
const obj = {};
const dict = Object.create(null);

// Wrapping values is ok
const str = Object("foo");
const num = Object(123);

function isObject(value) {
  return value === Object(value);
}
```