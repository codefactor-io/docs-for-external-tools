Pattern: Function inside loop

Issue: -

## Description

Writing functions within loops tends to result in errors due to the way
closures work in JavaScript. Functions capture variables by reference,
not by value. When using `var`, which is function-scoped, all iterations
share the same variable binding, leading to unexpected behavior.

## Examples

Example of **incorrect** code:
```javascript
for (var i = 0; i < 10; i++) {
  funcs[i] = function () {
    return i;
  };
}
```

Example of **correct** code:
```javascript
for (let i = 0; i < 10; i++) {
  funcs[i] = function () {
    return i;
  };
}
```
