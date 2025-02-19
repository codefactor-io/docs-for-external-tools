Pattern: Missing parameter type

Issue: -

## Description

Each @param tag must include a type specification in curly braces. Types provide important information about expected parameter values.

## Examples

Example of **incorrect** code:
```javascript
/**
 * @param name Name of the user
 * @param age Age of the user
 */
function createUser(name, age) {}
```

Example of **correct** code:
```javascript
/**
 * @param {string} name Name of the user
 * @param {number} age Age of the user
 */
function createUser(name, age) {}
```