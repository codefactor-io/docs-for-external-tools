Pattern: ES import with CommonJS export

Issue: -

## Description

This rule reports the use of import declarations with CommonJS exports in any module except for the main module (as defined in package.json). Mixing ES import syntax with CommonJS module.exports can lead to unexpected behavior, particularly with bundlers like webpack.

If you have multiple entry points or are using `js:next`, this rule includes an `exceptions` option which you can use to exclude those files from the rule.

## Examples

Example of **incorrect** code:
```js
import { stuff } from 'starwars'
module.exports = thing

import * as allThings from 'starwars'
exports.bar = thing

import thing from 'other-thing'
exports.foo = bar

import thing from 'starwars'
const baz = (module.exports = thing)
console.log(baz)
```

Example of **correct** code:
```js
import thing from 'other-thing'
export default thing

const thing = require('thing')
module.exports = thing

const thing = require('thing')
exports.foo = bar

import thing from 'otherthing'
console.log(thing.module.exports)
```

Example of **correct** code in the main module (given package.json with `"main": "lib/index.js"`):
```js
// in lib/index.js
import foo from 'path'
module.exports = foo
```

Example of **correct** code with exceptions:
```js
// in some-file.js
// eslint import-x/no-import-module-exports: ["error", {"exceptions": ["**/*/some-file.js"]}]
import foo from 'path'
module.exports = foo
```