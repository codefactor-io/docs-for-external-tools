Pattern: Constant expression in condition

Issue: -

## Description

Using constant expressions in conditions of if, for, while, do-while statements or ternary expressions is usually a mistake. These conditions will always evaluate to the same result, making the code branch either unreachable or creating an infinite loop.

## Examples

Example of **incorrect** code:
```javascript
if (false) {
  doSomething();
}

while (true) {
  doSomethingForever();
}

const value = true ? 1 : 2;

for (;-1;) {
  doSomethingForever();
}

if (new Boolean(x)) {
  doSomethingAlways();
}
```

Example of **correct** code:
```javascript
if (x === 0) {
  doSomething();
}

while (condition) {
  doSomething();
}

const value = condition ? 1 : 2;

for (;length > 0;) {
  doSomething();
}

if (Boolean(x)) {
  doSomething();
}
```