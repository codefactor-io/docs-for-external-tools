Pattern: Useless `return;`

Issue: -

## Description

A `return;` statement with nothing after it is redundant, and has no effect on the runtime behavior of a function. This can be confusing, so it's better to disallow these redundant statements.

## Examples

Example of **incorrect** code:

```js
function foo() {
  return;
}

function bar() {
  doSomething();
  return;
}

function baz() {
  if (condition) {
    doSomething();
    return;
  }
}
```

Example of **correct** code:

```js
function foo() {
  return 5;
}

function bar() {
  if (condition) {
    return;
  }
  doSomething();
}

function baz() {
  return doSomething();
}
```