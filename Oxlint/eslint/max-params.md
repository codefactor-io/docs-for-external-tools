Pattern: Function with too many parameters

Issue: -

## Description

Functions with numerous parameters are difficult to understand and use, as they require memorizing each parameter's type, purpose, and order. Large parameter lists often indicate that a function is doing too much or that its parameters should be refactored into an options object.

## Examples

Example of **incorrect** code:
```javascript
function foo(bar, baz, qux, qxx) {
  doSomething();
}

const process = (title, firstName, lastName, age, city, state, country) => {
  // ...
};
```

Example of **correct** code:
```javascript
function foo(bar, baz) {
  doSomething();
}

const process = (userInfo) => {
  const { title, firstName, lastName, age, address } = userInfo;
  // ...
};
```