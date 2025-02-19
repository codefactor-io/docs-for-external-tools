Pattern: Duplicate condition in if-else chain

Issue: -

## Description

Using identical conditions in an if-else-if chain is likely a mistake since the duplicate branch can never be reached. Unless the conditions have side effects, the repeated condition will evaluate to the same result as its first occurrence.

## Examples

Example of **incorrect** code:
```javascript
if (a) {
  foo();
} else if (b) {
  bar();
} else if (b) {  // Duplicate condition
  baz();
}

if (n > 10) {
  handleBig();
} else if (n < 5) {
  handleSmall();
} else if (n > 10) {  // Never reached
  handleOther();
}
```

Example of **correct** code:
```javascript
if (a) {
  foo();
} else if (b) {
  bar();
} else if (c) {
  baz();
}

if (n > 10) {
  handleBig();
} else if (n < 5) {
  handleSmall();
} else {
  handleOther();
}
```