Pattern: Assignment in return statement

Issue: -

## Description

Using assignments in return statements can lead to confusion, especially when a single equals sign is meant to be a comparison. The ambiguity between assignment and comparison makes code harder to understand and can introduce subtle bugs.

## Examples

Example of **incorrect** code:
```javascript
function setAndReturn() {
  return foo = 'bar';
}

const arrowFunc = () => x = y;

function addValue() {
  return counter += 1;
}

function process() {
  return result = someOperation();
}
```

Example of **correct** code:
```javascript
function setAndReturn() {
  foo = 'bar';
  return foo;
}

const arrowFunc = () => {
  x = y;
  return x;
};

function addValue() {
  counter += 1;
  return counter;
}

function process() {
  const result = someOperation();
  return result;
}
```