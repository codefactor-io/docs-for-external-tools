Pattern: Default export imported as named

Issue: -

## Description

This rule reports use of a default export as a locally named import. The rationale is that the syntax exists specifically to import default exports expressively, so we should use it directly.

Type imports, as used by Flow, are always ignored by this rule.

## Examples

Given a module file `foo.js`:
```js
export default 'foo'
export const bar = 'baz'
```

Example of **incorrect** code:
```js
import { default as foo } from './foo.js'
import { default as foo, bar } from './foo.js'
```

Example of **correct** code:
```js
import foo from './foo.js'
import foo, { bar } from './foo.js'
```