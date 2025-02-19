Pattern: Reassignment of function declaration

Issue: -

## Description

Reassigning a function that was created via a function declaration is usually a mistake. If you need to assign different functions to the same name, use a function expression with let/var instead.

## Examples

Example of **incorrect** code:
```javascript
function foo() {
  console.log("first");
}
foo = function() {
  console.log("second");
};

function bar() {}
if (condition) {
  bar = someOtherFunction;
}
```

Example of **correct** code:
```javascript
let foo = function() {
  console.log("first");
};
foo = function() {
  console.log("second");
};

// Or keep function declaration unmodified
function bar() {}
let alternateFn;
if (condition) {
  alternateFn = bar;
}
```