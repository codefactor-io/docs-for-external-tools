Pattern: Unresolved module import

Issue: -

## Description

This rule ensures an imported module can be resolved to a module on the local filesystem, as defined by standard Node `require.resolve` behavior. By default, it only checks ES6 imports, but can be configured to also check CommonJS and AMD imports.

The rule can be customized for resolution with settings for additional filetypes, `NODE_PATH`, etc. If you are using Webpack, see the documentation on resolvers.

## Examples

Example of **incorrect** code:
```js
import x from './foo' // Reported if './foo' cannot be resolved on the filesystem
```

Example of **incorrect** code with `{ commonjs: true }`:
```js
const { default: x } = require('./foo') // Reported if './foo' is not found
```

Example of **incorrect** code with `{ amd: true }`:
```js
define(['./foo'], function (foo) {
  /*...*/
}) // Reported if './foo' is not found

require(['./foo'], function (foo) {
  /*...*/
}) // Reported if './foo' is not found
```

Example of **incorrect** code with `{ caseSensitive: true }`:
```js
const { default: x } = require('./foo') // Reported if './foo' is actually './Foo' on the filesystem
```

Example of **incorrect** code with `{ caseSensitiveStrict: true }`:
```js
// Absolute paths
import Foo from `/Users/fOo/bar/file.js` // Reported (should be /Users/foo/bar/file.js)
import Foo from `d:/fOo/bar/file.js` // Reported (should be d:/foo/bar/file.js)

// Relative paths, cwd is Users/foo/
import Foo from `./../fOo/bar/file.js` // Reported (case mismatch)
```

Example of **correct** code:
```js
import x from './foo' // Not reported if './foo' can be resolved

// These are ignored by default (unless commonjs: true)
require(0)
require(['x', 'y'], function (x, y) {/*...*/})
```

Example of **correct** code with `{ ignore: ['\\.img$'] }`:
```js
import { x } from './mod' // May be reported if not resolved

import coolImg from '../../img/coolImg.img' // Will not be reported even if not found
```