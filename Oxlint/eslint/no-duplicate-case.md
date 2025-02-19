Pattern: Duplicate case in switch statement

Issue: -

## Description

Duplicate test expressions in switch statement case clauses are usually the result of copy-paste errors. Since the first matching case will execute, any duplicates that follow are unreachable code.

## Examples

Example of **incorrect** code:
```javascript
var a = 1, one = 1;

switch (a) {
  case 1:
    break;
  case 2:
    break;
  case 1:  // Duplicate case
    break;
}

switch (a) {
  case one:
    break;
  case 2:
    break;
  case one:  // Duplicate case
    break;
}
```

Example of **correct** code:
```javascript
var a = 1;

switch (a) {
  case 1:
    break;
  case 2:
    break;
  case 3:
    break;
}

switch (a) {
  case "1":
    break;
  case 1:
    break;  // Different type, not a duplicate
  default:
    break;
}
```