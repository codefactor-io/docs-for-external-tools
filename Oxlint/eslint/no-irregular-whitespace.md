Pattern: Non-standard whitespace character in code

Issue: -

## Description

Irregular whitespace characters (like non-breaking spaces, zero-width spaces, or various Unicode spaces) can cause visual inconsistencies and make code harder to maintain. These characters often appear when copying code from word processors or websites.

## Examples

Example of **incorrect** code:
```javascript
function foo() {　  // Has irregular space
  return 42;
}

const items = ['foo',　'bar'];  // Has irregular space

if (condition) {
  doSomething();⠀⠀// Has irregular spaces
}
```

Example of **correct** code:
```javascript
function foo() {  // Uses regular space
  return 42;
}

const items = ['foo', 'bar'];  // Uses regular space

if (condition) {
  doSomething();  // Uses regular spaces
}
```