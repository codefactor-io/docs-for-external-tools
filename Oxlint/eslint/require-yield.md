Pattern: Generator function without `yield`

Issue: -

## Description

Generator functions that don't use yield are likely a mistake. The purpose of a generator is to yield multiple values. A generator without yield could be written as a regular function returning a single value.

## Examples

Example of **incorrect** code:
```javascript
function* generator() {
  return 10;
}

function* emptyGen() {
}

const gen = function*() {
  doSomething();
};
```

Example of **correct** code:
```javascript
function* generator() {
  yield 1;
  yield 2;
  return 3;
}

function* range(start, end) {
  for (let i = start; i <= end; i++) {
    yield i;
  }
}

function* gen() {
  yield* otherGenerator();
}
```