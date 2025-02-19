Pattern: Missing return documentation

Issue: -

## Description

Functions that return values should document their return value with a @returns tag. Multiple @returns tags on the same function are not allowed.

## Examples

Example of **incorrect** code:
```javascript
/**
 * Process user data
 */
function processUser(user) {
  return user.id;
}

/**
 * @returns {string} User ID
 * @returns {number} User age
 */
function getUser() {
  return "123";
}
```

Example of **correct** code:
```javascript
/**
 * Process user data
 * @returns {string} User ID
 */
function processUser(user) {
  return user.id;
}
```