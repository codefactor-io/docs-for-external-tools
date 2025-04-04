Pattern: Deprecated import usage

Issue: -

## Description

This rule reports use of a deprecated name, as indicated by a JSDoc block with a `@deprecated` tag or TomDoc `Deprecated:` comment. It helps ensure that deprecated code is not used in new development.

Only JSDoc is enabled by default. Other documentation styles can be enabled with the `import-x/docstyle` setting.

## Examples

Example of **incorrect** code with a JSDoc `@deprecated` tag:
```js
// answer.js
/**
 * this is what you get when you trust a mouse talk show
 * @deprecated need to restart the experiment
 * @returns {Number} nonsense
 */
export function multiply(six, nine) {
  return 42
}

// main.js
import { multiply } from './answer' // Deprecated: need to restart the experiment

function whatever(y, z) {
  return multiply(y, z) // Deprecated: need to restart the experiment
}
```

Example of **incorrect** code with TomDoc comment:
```js
// answer.js
// Deprecated: This is what you get when you trust a mouse talk show, need to
// restart the experiment.
//
// Returns a Number nonsense
export function multiply(six, nine) {
  return 42
}

// main.js
import { multiply } from './answer' // Deprecated: This is what you get...

function whatever(y, z) {
  return multiply(y, z) // Deprecated: This is what you get...
}
```

Example of **correct** code:
```js
// Using non-deprecated exports
export function add(a, b) {
  return a + b
}

import { add } from './math'
```