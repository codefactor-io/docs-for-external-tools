Pattern: Missing property tags

Issue: -

## Description

Object type definitions using @typedef or @namespace must include @property tags when their type is Object, object, or PlainObject. This ensures the object's structure is properly documented.

## Examples

Example of **incorrect** code:
```javascript
/**
 * @typedef {Object} UserConfig
 */

/**
 * @namespace {object} Settings
 */
```

Example of **correct** code:
```javascript
/**
 * @typedef {Object} UserConfig
 * @property {string} username User's login name
 * @property {number} age User's age
 */

/**
 * @namespace {object} Settings
 * @property {boolean} darkMode Dark mode enabled
 */
```