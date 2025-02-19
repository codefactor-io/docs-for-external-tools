Pattern: Implements on non-constructor

Issue: -

## Description

The @implements tag should only be used on class constructors or functions marked with @class. Using it on regular functions is incorrect as they cannot implement interfaces.

## Examples

Example of **incorrect** code:
```javascript
/**
 * @implements {Interface}
 */
function normalFunction() {}
```

Example of **correct** code:
```javascript
/**
 * @implements {Interface}
 */
class MyClass {
  constructor() {}
}

/**
 * @implements {Interface}
 * @class
 */
function ClassFunction() {}
```