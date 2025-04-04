Pattern: Excessive module dependency

Issue: -

## Description

This rule forbids modules from having too many dependencies (`import` or `require` statements). A module with too many dependencies is a code smell, and usually indicates the module is doing too much and/or should be broken up into smaller modules.

Importing multiple named exports from a single module will only count once (e.g. `import {x, y, z} from './foo'` will only count as a single dependency).

## Examples

Example of **incorrect** code with `{"max": 2}`:
```js
import a from './a' // 1
const b = require('./b') // 2
import c from './c' // 3 - exceeds max!
```

Example of **correct** code with `{"max": 2}`:
```js
import a from './a' // 1
const anotherA = require('./a') // still 1
import { x, y, z } from './foo' // 2
```

Example of **incorrect** code with `{"max": 2, "ignoreTypeImports": true}`:
```ts
import a from './a'
import b from './b'
import c from './c'
```

Example of **correct** code with `{"max": 2, "ignoreTypeImports": true}`:
```ts
import a from './a'
import b from './b'
import type c from './c' // Doesn't count against max
```