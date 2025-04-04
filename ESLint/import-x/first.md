Pattern: Non-top import statement

Issue: -

## Description

This rule reports any imports that come after non-import statements. Since imports are hoisted, the imported modules will be evaluated before any of the statements interspersed between them. Keeping all imports together at the top of the file may prevent surprises resulting from this part of the specification.

Providing `absolute-first` as an option will report any absolute imports (i.e. packages) that come after any relative imports.

## Examples

Example of **incorrect** code:
```js
import foo from './foo'

// some module-level initializer
initWith(foo)

import bar from './bar' // <- reported
```

Example of **incorrect** code with `absolute-first` option:
```js
import foo from 'foo'
import bar from './bar'

import * as _ from 'lodash' // <- reported
```

Example of **correct** code:
```js
'use super-mega-strict' // directives are allowed before imports

import { suchFoo } from 'lame-fake-module-name'
import bar from './bar'

// module code starts here
initWith(suchFoo, bar)
```

Example of **correct** code with `absolute-first` option:
```js
import foo from 'foo'
import * as _ from 'lodash'
import bar from './bar'

// module code starts here
```