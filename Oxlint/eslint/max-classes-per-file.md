Pattern: Multiple classes in single file

Issue: -

## Description

Files containing multiple classes often become difficult to navigate and maintain. Following the single responsibility principle, each file should ideally contain only one class, making the codebase more organized and easier to understand.

## Examples

Example of **incorrect** code:
```javascript
class Foo {
  // ...
}

class Bar {
  // ...
}

class Baz {
  // ...
}
```

Example of **correct** code:
```javascript
// In foo.js
class Foo {
  // ...
}

// In bar.js
class Bar {
  // ...
}

// In baz.js
class Baz {
  // ...
}
```