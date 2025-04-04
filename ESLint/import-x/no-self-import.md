Pattern: Module self-import

Issue: -

## Description

This rule forbids a module from importing itself. This can sometimes happen during refactoring and lead to circular dependency issues that may not be immediately obvious.

## Examples

Example of **incorrect** code:
```js
// foo.js
import foo from './foo'

// foo.js
const foo = require('./foo')
```

```js
// index.js
import index from '.'

// index.js
const index = require('.')
```

Example of **correct** code:
```js
// foo.js
import bar from './bar'

// foo.js
const bar = require('./bar')
```