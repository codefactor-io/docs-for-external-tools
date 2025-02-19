Pattern: Assignment of `this` to variable

Issue: -

## Description

Storing `this` in a variable creates unnecessary aliases that can make code more confusing. Instead, use proper binding techniques or pass `this` as a parameter when needed.

## Examples

Example of **incorrect** code:
```javascript
const foo = this;
class Bar {
  method() {
    foo.baz();
  }
}

new Bar().method();
```

Example of **correct** code:
```javascript
class Bar {
  constructor(fooInstance) {
    this.fooInstance = fooInstance;
  }
  method() {
    this.fooInstance.baz();
  }
}

new Bar(this).method();
```