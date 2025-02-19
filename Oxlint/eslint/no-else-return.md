Pattern: `else` block after `return` in `if` statement

Issue: -

## Description

When an `if` block contains a `return` statement, the subsequent `else` block becomes unnecessary. The code in the `else` block can be placed outside the `if` statement since the `return` already exits the function when the `if` condition is true.

## Examples

Example of **incorrect** code:
```javascript
function foo() {
  if (x) {
    return y;
  } else {
    return z;
  }
}

function process(error) {
  if (error) {
    return "Failed";
  } else {
    if (loading) {
      return "Loading";
    }
  }
}
```

Example of **correct** code:
```javascript
function foo() {
  if (x) {
    return y;
  }
  return z;
}

function process(error) {
  if (error) {
    return "Failed";
  }
  if (loading) {
    return "Loading";
  }
}
```