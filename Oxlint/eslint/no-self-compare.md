Pattern: Variable compared to itself

Issue: -

## Description

Comparing a variable with itself is usually a mistake, either a typo or refactoring error. Such comparisons are either always true for equality or always false for inequality, making them logically meaningless.

## Examples

Example of **incorrect** code:
```javascript
var x = 10;
if (x === x) {
  doSomething();
}

if (obj.prop !== obj.prop) {
  handle();
}

if (arr[0] >= arr[0]) {
  process();
}
```

Example of **correct** code:
```javascript
var x = 10;
var y = 20;
if (x === y) {
  doSomething();
}

if (obj.prop !== obj.otherProp) {
  handle();
}

if (arr[0] >= arr[1]) {
  process();
}
```