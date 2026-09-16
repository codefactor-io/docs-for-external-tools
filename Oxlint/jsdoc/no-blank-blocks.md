Pattern: Blank JSDoc block

Issue: -

## Description

Blank JSDoc blocks add noise without providing any documentation.

## Examples

Example of **incorrect** code:
```javascript
/** */

/**
 *
 */
```

Example of **correct** code:
```javascript
/** @tag */

/**
 * Text
 */

/**
 * @tag
 */
```
