Pattern: Inconsistent function declaration style

Issue: -

## Description

Mixing function declarations and function expressions in a codebase reduces consistency and can lead to confusion about hoisting behavior. The rule can be configured to enforce either declarations or expressions as the preferred style.

## Examples

Example of **incorrect** code:
```javascript
// When configured for expressions
function foo() {
  // ...
}

// When configured for declarations
const foo = function() {
  // ...
};

const bar = () => {
  // ...
};
```

Example of **correct** code:
```javascript
// When configured for expressions
const foo = function() {
  // ...
};

// When configured for declarations
function foo() {
  // ...
}

// Methods are not checked
SomeObject.foo = function() {
  // ...
};
```