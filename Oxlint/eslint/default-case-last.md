Pattern: `default` clause not at end of `switch`

Issue: -

## Description

A switch statement's default clause is expected to be the last clause by convention. While it can be placed anywhere and will only execute when no case matches, having it before or between cases creates confusing control flow and reduces code readability.

## Examples

Example of **incorrect** code:
```javascript
switch (foo) {
  default:
    bar();
    break;
  case "a":
    baz();
    break;
}

switch (foo) {
  case 1:
    bar();
    break;
  default:
    baz();
    break;
  case 2:
    qux();
    break;
}
```

Example of **correct** code:
```javascript
switch (foo) {
  case "a":
    baz();
    break;
  default:
    bar();
    break;
}

switch (foo) {
  case 1:
    bar();
    break;
  case 2:
    qux();
    break;
  default:
    baz();
    break;
}
```