Pattern: Use of `this` before `super()` call

Issue: -

## Description

In derived class constructors, `super()` must be called before accessing `this` or `super`. Accessing `this` before `super()` is called will throw a reference error as the object is not yet initialized.

## Examples

Example of **incorrect** code:
```javascript
class Animal extends Living {
  constructor() {
    this.legs = 4;  // ReferenceError
    super();
  }
}

class Dog extends Animal {
  constructor() {
    this.bark();  // ReferenceError
    super();
    this.legs = 4;
  }
}
```

Example of **correct** code:
```javascript
class Animal extends Living {
  constructor() {
    super();
    this.legs = 4;  // Valid after super()
  }
}

class Dog extends Animal {
  constructor() {
    super();
    this.bark();  // Valid after super()
    this.legs = 4;
  }
}
```