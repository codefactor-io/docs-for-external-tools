Pattern: Mutable declaration without reassignment

Issue: -

## Description

If a variable is never reassigned, using the `const` declaration is better.
`const` declaration tells readers, "this variable is never reassigned," reducing cognitive load and improving maintainability.

## Examples

Example of **incorrect** code:
```javascript
let a = 3;
console.log(a);

let b;
b = 0;
console.log(b);

for (let i in [1, 2, 3]) {
  console.log(i);
}
```

Example of **correct** code:
```javascript
const a = 0;

let a;
a = 0;
a = 1;

let a;
if (true) {
  a = 0;
}

for (const i in [1, 2, 3]) {
  console.log(i);
}
```
