Pattern: Inconsistent switch case braces

Issue: -

## Description

Empty switch cases should not have braces to reduce visual clutter, while non-empty cases should have braces to properly scope their contents. This makes switch statements more readable and maintainable.

## Examples

Example of **incorrect** code:
```javascript
switch (num) {
  case 1: {
  }
  case 2:
    console.log("Case 2");
    break;
}
```

Example of **correct** code:
```javascript
switch (num) {
  case 1: 
  case 2: {
    console.log("Case 2");
    break;
  }
}
```