Pattern: Named export used as default import name

Issue: -

## Description

Using the name of a module's named export as the identifier when importing its default export can be misleading and confusing. This pattern often indicates a mistake where the developer intended to import the named export but forgot the curly braces.

## Examples

Example of **incorrect** code:
```javascript
// foo.js
export default 'foo'
export const bar = 'baz'

// Importing file
import bar from './foo.js'
```

Example of **correct** code:
```javascript
// foo.js
export default 'foo'
export const bar = 'baz'

// Importing file
import foo from './foo.js'
import { bar } from './foo.js'
```