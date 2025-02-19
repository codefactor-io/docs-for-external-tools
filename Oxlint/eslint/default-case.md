Pattern: Missing `default` clause in `switch` statement

Issue: -

## Description

Switch statements should include a default case to handle unexpected input values. Even if the default case is empty, its presence makes the code's intent explicit and helps prevent bugs from unhandled cases.

## Examples

Example of **incorrect** code:
```javascript
switch (foo) {
  case 1:
    break;
}
```

Example of **correct** code:
```javascript
switch (foo) {
  case 1:
    break;
  default:
    // handle unexpected values
    break;
}
```