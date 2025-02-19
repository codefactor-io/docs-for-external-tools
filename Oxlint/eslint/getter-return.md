Pattern: Missing return in getter

Issue: -

## Description

Getter methods are expected to return values. A getter without a return statement is likely a mistake. Note: This rule does not run on TypeScript files since type checking will catch getters that do not return a value.

## Examples

Example of **incorrect** code:
```javascript
class Person {
  get name() {
    // no return
  }
}

const obj = {
  get foo() {
    // object getter are also checked
  },
};
```

Example of **correct** code:
```javascript
class Person {
  get name() {
    return this._name;
  }
}
```