Pattern: Reference to undeclared variable

Issue: -

## Description

Using variables that have not been declared leads to a ReferenceError at runtime. This often happens due to typos in variable names or forgetting to import or declare a variable. Always declare variables before use.

## Examples

Example of **incorrect** code:
```javascript
function foo() {
  bar = 3;  // bar is not declared
}

console.log(undeclared);

if (someUndefined) {
  handleCase();
}

obj.someFunction();  // obj is not declared

const sum = a + b;  // a and b are not declared
```

Example of **correct** code:
```javascript
let bar;
function foo() {
  bar = 3;
}

const undeclared = 'now declared';
console.log(undeclared);

const someUndefined = condition;
if (someUndefined) {
  handleCase();
}

const obj = {};
obj.someFunction();

const a = 1, b = 2;
const sum = a + b;
```