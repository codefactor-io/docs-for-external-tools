Pattern: Empty `case` before `default` in switch statement

Issue: -

## Description

An empty `case` statement placed just before a `default` case is redundant since the `default` case will handle all unmatched values anyway.

## Examples

Example of **incorrect** code:
```javascript
switch (foo) {
  case 1:
  default:
    handleDefaultCase();
    break;
}
```

Example of **correct** code:
```javascript
switch (foo) {
  case 1:
  case 2:
    handleCase1And2();
    break;
}
```