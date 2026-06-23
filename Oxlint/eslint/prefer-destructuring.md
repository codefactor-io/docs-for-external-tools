Pattern: Missing use of destructuring

Issue: -

## Description

With JavaScript ES2015, a new syntax was added for creating variables from an array index or object property,
called destructuring. This rule enforces usage of destructuring
instead of accessing a property through a member expression.

## Examples

Example of **incorrect** code:
```javascript
// With `array` enabled
const foo = array[0];
bar.baz = array[0];
// With `object` enabled
const qux = object.qux;
const quux = object["quux"];
```

Example of **correct** code:
```javascript
// With `array` enabled
const [foo] = array;
const arr = array[someIndex];
[bar.baz] = array;

// With `object` enabled
const { baz } = object;
const obj = object.bar;
```
