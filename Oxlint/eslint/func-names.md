Pattern: Anonymous function expression 

Issue: -

## Description

Anonymous functions show up as '<anonymous>' in stack traces, making it difficult to debug errors. Named function expressions provide better stack traces by including the function name, making it easier to identify where an error occurred.

## Examples

Example of **incorrect** code:
```javascript
Foo.prototype.bar = function() {};

const handler = function() {
  throw new Error('Something went wrong');
};
```

Example of **correct** code:
```javascript
Foo.prototype.bar = function bar() {};

const handler = function errorHandler() {
  throw new Error('Something went wrong');
};
```