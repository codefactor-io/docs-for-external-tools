Pattern: Callback invocation without `return`

Issue: -

## Description

This rule is aimed at ensuring that callbacks used outside of the main function block are always part-of or immediately preceding a `return` statement.
This rule decides what is a callback based on the name of the function being called.

## Examples

Example of **incorrect** code:
```javascript
function done(err) {
  if (err) {
    callback(err);
  }
  callback();
}
```

Example of **correct** code:
```javascript
function done(err) {
  if (err) {
    return callback(err);
  }
  callback();
}
```
