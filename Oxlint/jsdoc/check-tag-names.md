Pattern: Invalid JSDoc tag

Issue: -

## Description

Using invalid or unknown JSDoc tags, or tags that are redundant when using TypeScript, reduces documentation clarity and can lead to confusion.

## Examples

Example of **incorrect** code:
```javascript
/**
 * @Param {string} name - Incorrect capitalization
 * @foo - Unknown tag
 * @type {string} - Redundant with TypeScript
 */
function greet(name) {
  return `Hello ${name}`;
}
```

Example of **correct** code:
```javascript
/**
 * @param {string} name - The name to greet
 * @returns {string} The greeting message
 */
function greet(name) {
  return `Hello ${name}`;
}
```