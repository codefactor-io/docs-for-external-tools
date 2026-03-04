Pattern: Passing function to iterator method

Issue: -

## Description

Passing functions to iterator methods can cause issues when the function is changed without realizing that the iterator passes 2 more parameters to it (index and array). This can lead to unexpected behavior when the function signature changes.

## Examples

Example of **incorrect** code:

```javascript
const foo = array.map(callback);
array.forEach(callback);
const result = array.filter(lib.method);
```

Example of **correct** code:

```javascript
const foo = array.map((element) => callback(element));
array.forEach((element) => {
  callback(element);
});
const result = array.filter((element) => lib.method(element));

// Built-in functions are allowed
const foo = array.map(String);
const bar = array.filter(Boolean);
```