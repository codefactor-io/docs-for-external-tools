Pattern: Return statement in constructor

Issue: -

## Description

Class constructors in JavaScript implicitly return the constructed object instance. Explicitly returning a value from a constructor may indicate a misunderstanding of class construction or a copy-paste error from a regular function.

## Examples

Example of **incorrect** code:
```javascript
class A {
  constructor() {
    return 42;
  }
}

class B {
  constructor() {
    return { custom: 'object' };
  }
}
```

Example of **correct** code:
```javascript
class A {
  constructor() {
    this.value = 42;
  }
}

class B {
  constructor() {
    this.custom = 'object';
  }
}
```