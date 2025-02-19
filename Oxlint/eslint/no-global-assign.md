Pattern: Assignment to read-only global variable

Issue: -

## Description

Assigning values to built-in global variables (like Object, Array, String) can break the functionality of these essential objects throughout the application. These globals are meant to be read-only references to core JavaScript functionality.

## Examples

Example of **incorrect** code:
```javascript
Object = null;
Array = 1;
undefined = 42;
Math = {};
window = {};

Object = function() {};
String = "not a constructor";
```

Example of **correct** code:
```javascript
myObject = null;
array = 1;
undefined_var = 42;

const Math = {};  // Local variable shadowing is fine
let String = 'str';  // Block-scoped variable
```