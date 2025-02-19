Pattern: Unsorted object property keys

Issue: -

## Description

When an object has multiple properties, keeping the keys in alphabetical order makes it easier to find specific properties and spot differences when comparing objects. Consistent sorting improves code readability and maintainability.

## Examples

Example of **incorrect** code:
```javascript
const user = {
  name: 'John',
  age: 30,
  id: 1
};

let config = {
  zoom: 100,
  width: 800,
  theme: 'dark',
  height: 600
};
```

Example of **correct** code:
```javascript
const user = {
  age: 30,
  id: 1,
  name: 'John'
};

let config = {
  height: 600,
  theme: 'dark',
  width: 800,
  zoom: 100
};
```