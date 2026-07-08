Pattern: Unmodified loop condition

Issue: -

## Description

A loop condition that depends on values that never change within the loop body
can cause infinite loops or logic bugs.

## Examples

Example of **incorrect** code:
```javascript
let done = false;
while (!done) {
  work();
}
```

Example of **correct** code:
```javascript
let done = false;
while (!done) {
  done = checkDone();
}
```
