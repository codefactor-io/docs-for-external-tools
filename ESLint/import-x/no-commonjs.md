Pattern: CommonJS module syntax

Issue: -

## Description

This rule reports `require([string])` function calls and `module.exports` or `exports.*` usage. It will not report if the `require` call has more than one argument, or if the single argument is not a literal string.

This rule is intended for temporary use when migrating from CommonJS to pure ES6 modules.

## Examples

Example of **incorrect** code:
```js
var mod = require('./mod'),
  common = require('./common'),
  fs = require('fs'),
  whateverModule = require('./not-found')

module.exports = { a: 'b' }
exports.c = 'd'
```

Example of **correct** code with `{ allowRequire: true }`:
```js
var mod = require('./mod')
```

Example of **correct** code (by default, conditional requires are allowed):
```js
var a = b && require('c')

if (typeof window !== 'undefined') {
  require('that-ugly-thing')
}

var fs = null
try {
  fs = require('fs')
} catch (error) {}
```

Example of **incorrect** code with `{ allowConditionalRequire: false }`:
```js
var a = b && require('c')

if (typeof window !== 'undefined') {
  require('that-ugly-thing')
}
```

Example of **correct** code with `{ allowPrimitiveModules: true }`:
```js
module.exports = 'foo'

module.exports = function rule(context) {
  return {
    /* ... */
  }
}
```

Example of **incorrect** code even with `{ allowPrimitiveModules: true }`:
```js
module.exports = { x: 'y' }

exports.z = function boop() {
  /* ... */
}
```