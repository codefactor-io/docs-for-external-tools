Pattern: Undocumented parameter

Issue: -

## Description

All function parameters must be documented with @param tags. Missing documentation makes it harder for other developers to understand how to use the function.

## Examples

Example of **incorrect** code:
```javascript
/**
 * @param {string} name User's name
 */
function createUser(name, age, role) {}
```

Example of **correct** code:
```javascript
/**
 * @param {string} name User's name
 * @param {number} age User's age
 * @param {string} role User's role
 */
function createUser(name, age, role) {}
```