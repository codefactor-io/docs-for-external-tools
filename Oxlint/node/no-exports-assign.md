Pattern: Direct exports assignment

Issue: -

## Description

Assigning directly to exports (exports = {}) can break module exports by replacing the exports object. Use module.exports or add properties to exports instead.

## Examples

Example of **incorrect** code:
```javascript
exports = {
  foo: 1,
  bar: 2
};

exports = function() {};
```

Example of **correct** code:
```javascript
module.exports = {
  foo: 1,
  bar: 2
};

exports.foo = 1;
exports.bar = 2;

// Allowed when used together
module.exports = exports = {};
```