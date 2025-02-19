Pattern: Empty function body

Issue: -

## Description

Empty functions reduce code readability as it's unclear whether the emptiness is intentional. If a function is meant to be empty, adding a comment explaining why improves code clarity and maintainability.

## Examples

Example of **incorrect** code:
```javascript
function foo() {}

const bar = () => {};

class MyClass {
  constructor() {}
  method() {}
}
```

Example of **correct** code:
```javascript
function foo() {
  // Used as a placeholder for future implementation
}

const bar = () => {
  // Event handler required by API
};

function process(data) {
  return data.map(item => item.id);
}
```