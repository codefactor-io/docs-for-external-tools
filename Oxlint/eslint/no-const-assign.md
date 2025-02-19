Pattern: Reassignment of `const` variable

Issue: -

## Description

Variables declared with `const` cannot be reassigned. Attempting to modify a `const` variable will raise a runtime error. Use `let` or `var` instead if the variable needs to be reassigned.

## Examples

Example of **incorrect** code:
```javascript
const a = 0;
a = 1;

const b = 0;
b += 1;

const obj = {};
obj = { prop: 1 };
```

Example of **correct** code:
```javascript
const a = 0;
console.log(a);

let b = 0;
b += 1;

const obj = {};
obj.prop = 1;  // Modifying properties is allowed
```