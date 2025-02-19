Pattern: Invalid property documentation

Issue: -

## Description

Property names in JSDoc must not be duplicated within the same block, and nested properties must have their parent properties defined as objects.

## Examples

Example of **incorrect** code:
```javascript
/**
 * @typedef {object} Config
 * @property {string} name
 * @property {number} name
 * @property {string} deep.nested.prop
 */
```

Example of **correct** code:
```javascript
/**
 * @typedef {object} Config
 * @property {string} name
 * @property {object} deep
 * @property {object} deep.nested
 * @property {string} deep.nested.prop
 */
```