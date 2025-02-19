Pattern: Lexical declaration in switch case

Issue: -

## Description

Lexical declarations (let, const, class) in case clauses create variables that are visible in the entire switch block but only initialized when the case is reached. This can lead to reference errors if the case is not executed.

## Examples

Example of **incorrect** code:
```javascript
switch (foo) {
  case 1:
    let x = 1;
    break;
  case 2:
    const y = 2;
    break;
  case 3:
    function f() {}
    break;
  default:
    class C {}
}
```

Example of **correct** code:
```javascript
switch (foo) {
  case 1: {
    let x = 1;
    break;
  }
  case 2: {
    const y = 2;
    break;
  }
  case 3: {
    function f() {}
    break;
  }
  default: {
    class C {}
  }
}
```