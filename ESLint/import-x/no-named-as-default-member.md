Pattern: Named export accessed as property of default export

Issue: -

## Description

This rule reports use of an exported name as a property on the default export. This is likely a mistake because named export syntax looks very similar to destructuring assignment, making it easy to incorrectly assume that named exports are also accessible as properties of the default export.

In Babel 5, named exports were actually accessible as properties of the default export, but this behavior was fixed in Babel 6. This rule is particularly useful when upgrading an existing codebase to Babel 6.

## Examples

Given a module file `foo.js`:
```js
export default 'foo'
export const bar = 'baz'
```

Example of **incorrect** code:
```js
import foo from './foo.js'
const bar = foo.bar // Caution: `foo` also has a named export `bar`

// Or with destructuring
import foo from './foo.js'
const { bar } = foo // Caution: `foo` also has a named export `bar`
```

Example of **correct** code:
```js
import foo, { bar } from './foo.js'
```