Pattern: Missing return description

Issue: -

## Description

The @returns tag must include a description of the return value unless the function returns void or undefined. Descriptions help other developers understand what the returned value represents.

## Examples

Example of **incorrect** code:
```javascript
/**
 * Process user data
 * @param {Object} user User object
 * @returns {string}
 */
function getUserId(user) {
  return user.id;
}
```

Example of **correct** code:
```javascript
/**
 * Process user data
 * @param {Object} user User object
 * @returns {string} The unique identifier for the user
 */
function getUserId(user) {
  return user.id;
}
```