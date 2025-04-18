Pattern: Dynamic require statement

Issue: -

## Description

Enforce a convention in the order of `require()` / `import` statements.

With the `groups` option set to `["builtin", "external", "internal", "parent", "sibling", "index", "object", "type"]` the order is as shown in the following example:

```ts
// 1. node "builtin" modules
import fs from 'fs'
import path from 'path'
// 2. "external" modules
import _ from 'lodash'
import chalk from 'chalk'
// 3. "internal" modules
// (if you have configured your path or webpack to handle your internal paths differently)
import foo from 'src/foo'
// 4. modules from a "parent" directory
import foo from '../foo'
import qux from '../../foo/qux'
// 5. "sibling" modules from the same or a sibling's directory
import bar from './bar'
import baz from './bar/baz'
// 6. "index" of the current directory
import main from './'
// 7. "object"-imports (only available in TypeScript)
import log = console.log
// 8. "type" imports (only available in Flow and TypeScript)
import type { Foo } from 'foo'
```

## Examples

Example of **incorrect** code:

```ts
import _ from 'lodash'
import path from 'path' // `path` import should occur before import of `lodash`

// -----

var _ = require('lodash')
var path = require('path') // `path` import should occur before import of `lodash`

// -----

var path = require('path')
import foo from './foo' // `import` statements must be before `require` statement
```

Example of **correct** code:

```ts
import path from 'path'
import _ from 'lodash'

// -----

var path = require('path')
var _ = require('lodash')

// -----

// Allowed as ̀`babel-register` is not assigned.
require('babel-register')
var path = require('path')

// -----

// Allowed as `import` must be before `require`
import foo from './foo'
var path = require('path')
```