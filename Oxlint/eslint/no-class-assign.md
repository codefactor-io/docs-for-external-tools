Pattern: Reassignment of class identifier

Issue: -

## Description

A class declaration creates a variable that technically can be reassigned, but doing so is almost always a mistake. The reassignment breaks the reference to the original class, causing errors when trying to create new instances.

## Examples

Example of **incorrect** code:
```javascript
class A {}
A = 123;
let a = new A();  // TypeError: A is not a constructor

class B {}
B = class C {};
```

Example of **correct** code:
```javascript
class A {}
let a = new A();

let B = class {};
B = class {};  // Allowed because B is not a class declaration
```