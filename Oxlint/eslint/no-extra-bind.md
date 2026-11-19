Pattern: Unnecessary `.bind()`

Issue: -

## Description

This rule is aimed at avoiding the unnecessary use of `bind()`
and as such will warn whenever an immediately-invoked function expression (IIFE) is using `bind()`
and doesn’t have an appropriate `this` value.
This rule won’t flag usage of `bind()` that includes function argument binding.

## Examples

Example of **incorrect** code:
```javascript
const x = function () {
  foo();
}.bind(bar);

const z = (() => {
  this.foo();
}).bind(this);
```

Example of **correct** code:
```javascript
const x = function () {
  this.foo();
}.bind(bar);
const y = function (a) {
  return a + 1;
}.bind(foo, bar);
```
