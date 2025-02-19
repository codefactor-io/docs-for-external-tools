Pattern: Class with only static members

Issue: -

## Description

A class that only contains static members can be replaced with a simpler object literal. Exception: classes with private static fields still need to be classes.

## Examples

Example of **incorrect** code:
```javascript
class A {
  static a() {}
  static b = 1;
}
```

Example of **correct** code:
```javascript
class A {
  static a() {}
  constructor() {}
}

const obj = {
  a() {},
  b: 1
};

class X {
  static #foo = false; // private field
  static bar() {}
}
```