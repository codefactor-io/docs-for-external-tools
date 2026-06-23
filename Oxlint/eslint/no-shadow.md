Pattern: Variable declaration shadowing outer scope

Issue: -

## Description

Shadowing is the process by which a local variable shares the same name as a variable
in its containing scope. This can cause confusion, as it may be unclear which variable
is being referenced, and can lead to bugs that are difficult to diagnose.

## Examples

Example of **incorrect** code:
```javascript
var x = 1;
function foo() {
  var x = 2; // x shadows the outer x
}
```

Example of **correct** code:
```javascript
var x = 1;
function foo() {
  var y = 2; // different name, no shadowing
}
```
