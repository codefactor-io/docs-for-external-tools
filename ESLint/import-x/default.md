Pattern: Missing default export

Issue: -

## Description

This rule reports if a default import is requested but there is no default export in the imported module. For ES7, it also reports if a default is named and exported but is not found in the referenced module.

The plugin will find exported names from `jsnext:main` in the package.json if present. A module path that is ignored or not unambiguously an ES module will not be reported when imported.

## Examples

Given:
```js
// ./foo.js
export default function () {
  return 42
}

// ./bar.js
export function bar() {
  return null
}

// ./baz.js
module.exports = function () {
  /* ... */
}
```

Example of **incorrect** code:
```js
import bar from './bar' // no default export found in ./bar
import baz from './baz' // no default export found in ./baz
```

Example of **correct** code:
```js
import foo from './foo'

// assuming 'node_modules' are ignored (true by default)
import someModule from 'some-module'
```