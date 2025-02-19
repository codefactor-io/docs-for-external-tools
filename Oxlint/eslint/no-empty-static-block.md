Pattern: Empty static initialization block

Issue: -

## Description

Empty static blocks in classes are likely the result of incomplete refactoring and serve no purpose. They should either be removed or documented with a comment explaining their intended use.

## Examples

Example of **incorrect** code:
```javascript
class Foo {
  static {}
}

class Bar {
  static {
  }
}
```

Example of **correct** code:
```javascript
class Foo {
  static {
    // Reserved for future initialization logic
  }
}

class Bar {
  static {
    initializeStaticFields();
  }
}

class Baz {
  // No static block needed
}
```