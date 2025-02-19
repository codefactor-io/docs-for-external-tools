Pattern: Redefinition of built-in global name

Issue: -

## Description

Redefining built-in globals like `undefined`, `NaN`, `Infinity`, `eval`, and `arguments` can break code in unexpected ways. These identifiers have special meaning in JavaScript and should not be used as variable names, parameters, or catch clause bindings.

## Examples

Example of **incorrect** code:
```javascript
function undefined() {}
var NaN = 5;
let Infinity = 42;

function test(eval) {
  console.log(eval);
}

try {
  throw new Error();
} catch(arguments) {
  console.log(arguments);
}
```

Example of **correct** code:
```javascript
function myFunc() {}
var notANumber = 5;
let counter = 42;

function test(evalParam) {
  console.log(evalParam);
}

try {
  throw new Error();
} catch(error) {
  console.log(error);
}
```