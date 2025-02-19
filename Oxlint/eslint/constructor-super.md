Pattern: Missing `super()` in derived class constructor

Issue: -

## Description

When a class extends another class, the constructor must call super() to execute the parent class's constructor. Failing to do so will cause a runtime error.

## Examples

Example of **incorrect** code:
```javascript
class A extends B {
  constructor() {
    // no super() call
  }
}
```

Example of **correct** code:
```javascript
class A extends B {
  constructor() {
    super();
  }
}
```