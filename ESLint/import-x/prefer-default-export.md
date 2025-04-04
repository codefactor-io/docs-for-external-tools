Pattern: Named export without default export

Issue: -

## Description

This rule checks if there is a default export in exporting files. It can be configured to either report when a file has only a single named export (and no default export), or to report any file that has exports but no default export.

The rule supports two configuration options:
- `target`: "single" (default) or "any"
  - "single": When there is only a single export from a module, prefer using default export over named export
  - "any": Any exporting file must contain a default export

## Examples

Example of **incorrect** code with `{ "target": "single" }`:
```javascript
// There is only a single module export and it's a named export
export const foo = 'foo'
```

Example of **correct** code with `{ "target": "single" }`:
```javascript
// There is a default export
export const foo = 'foo'
const bar = 'bar'
export default bar

// There is more than one named export in the module
export const foo = 'foo'
export const bar = 'bar'

// There is more than one named export in the module
const foo = 'foo'
const bar = 'bar'
export { foo, bar }

// There is a default export
const foo = 'foo'
export { foo as default }

// Any batch export will disable this rule
export * from './other-module'
```

Example of **incorrect** code with `{ "target": "any" }`:
```javascript
// Has 2 named exports, but no default export
export const foo = 'foo'
export const bar = 'bar'

// Does not have default export
let foo, bar
export { foo, bar }

// Does not have default export
export { a, b } from 'foo.js'

// Does not have default export
let item
export const foo = item
export { item }
```

Example of **correct** code with `{ "target": "any" }`:
```javascript
// Has default export
export default function bar() {}

// Has default export
let foo
export { foo as default }

// Contains multiple exports AND default export
export const a = 5
export function bar() {}
let foo
export { foo as default }

// Does not contain any exports => file is not checked by the rule
import * as foo from './foo'

// Any batch export will disable this rule
export * from './other-module'
```