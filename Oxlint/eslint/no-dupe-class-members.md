Pattern: Duplicate class member declaration

Issue: -

## Description

When class members have the same name, the last declaration silently overwrites previous ones. This can lead to unexpected behavior, especially when mixing methods and properties with the same name.

## Examples

Example of **incorrect** code:
```javascript
class A {
  foo() {
    console.log("foo");
  }
  foo = 123;  // Overwrites foo method
}

class B {
  bar() {}
  bar() {}  // Duplicate method
}
```

Example of **correct** code:
```javascript
class A {
  foo() {
    console.log("foo");
  }
  bar = 123;
}

class B {
  bar() {}
  baz() {}
}
```