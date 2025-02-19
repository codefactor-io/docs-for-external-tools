Pattern: Default parameter before required parameters

Issue: -

## Description

When default parameters appear before required parameters in a function signature, it becomes impossible to omit the optional arguments when calling the function. This forces developers to explicitly pass undefined for optional parameters.

## Examples

Example of **incorrect** code:
```javascript
function createUser(isAdmin = false, id) {}
createUser(undefined, "tabby");
```

Example of **correct** code:
```javascript
function createUser(id, isAdmin = false) {}
createUser("tabby");
```