Pattern: Empty named import block

Issue: -

## Description

This rule reports the use of empty named import blocks. Empty named import blocks (`import {} from 'mod'`) add unnecessary code and can indicate confusion about how to properly import from a module.

## Examples

Example of **incorrect** code:
```js
import {} from 'mod'
import Default from 'mod'
```

Example of **incorrect** code when using TypeScript:
```js
import type Default, {} from 'mod'
import type {} from 'mod'
```

Example of **incorrect** code when using Flow:
```js
import typeof {} from 'mod'
import typeof Default, {} from 'mod'
```

Example of **correct** code:
```js
import { mod } from 'mod'
import Default, { mod } from 'mod'
```

Example of **correct** code when using TypeScript:
```js
import type { mod } from 'mod'
```

Example of **correct** code when using Flow:
```js
import typeof { mod } from 'mod'
```