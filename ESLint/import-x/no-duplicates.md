Pattern: Duplicate module import

Issue: -

## Description

This rule reports if a resolved path is imported more than once. Unlike ESLint's core `no-duplicate-imports` rule, this version:

1. Reports duplicates even when the paths in the source code don't exactly match, as long as they point to the same module on the filesystem (e.g., `./foo` and `./foo.js`)
2. Distinguishes Flow `type` imports from standard imports

Duplicate imports are usually a result of two developers importing different names from the same module at different times and potentially different locations in the file. This rule helps identify these cases.

## Examples

Example of **incorrect** code:
```js
import SomeDefaultClass from './mod'

// oops, some other import separated these lines
import foo from './some-other-mod'

import * as names from './mod'

// will catch this too, assuming it is the same target module
import { something } from './mod.js'
```

Example of **correct** code:
```js
import SomeDefaultClass, * as names from './mod'
// Flow `type` import from same module is fine
import type SomeType from './mod'
```

Example of **correct** code with `{ "considerQueryString": true }`:
```js
import minifiedMod from './mod?minify'
import noCommentsMod from './mod?comments=0'
import originalMod from './mod'
```

Example of **incorrect** code with `{ "prefer-inline": true }`:
```js
import { AValue, type AType } from './mama-mia'
import type { BType } from './mama-mia'

import { CValue } from './papa-mia'
import type { CType } from './papa-mia'
```

Example of **correct** code with `{ "prefer-inline": true }`:
```js
import { AValue, type AType, type BType } from './mama-mia'

import { CValue, type CType } from './papa-mia'
```