Pattern: Nested solitary `if` statement

Issue: -

## Description

Having an `if` statement as the only statement inside another `if` block without `else` reduces readability. These conditions should be combined using logical operators.

## Examples

Example of **incorrect** code:
```javascript
if (foo) {
  if (bar) {
  }
}

if (foo) if (bar) baz();
```

Example of **correct** code:
```javascript
if (foo && bar) {
}

if (foo && bar) baz();
```