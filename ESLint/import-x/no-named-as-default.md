Pattern: Named export used as default import name

Issue: -

## Description

This rule reports use of an exported name as the locally imported name of a default export. This pattern is problematic because:

- It's misleading: others familiar with the module probably expect the name to be something else
- It's likely a mistake: the developer may have only needed to import the named export and forgot the brackets

For post-ES2015 `export` extensions, this also prevents exporting the default from a referenced module as a name within that module, for the same reasons.

## Examples

Given a module file `foo.js`:
```js
export default 'foo'
export const bar = 'baz'
```

Example of **incorrect** code:
```js
import bar from './foo.js' // Using exported name 'bar' as identifier for default export
```

Example of **correct** code:
```js
import foo from './foo.js'
```

For export extensions:

Example of **incorrect** code:
```js
export bar from './foo.js' // Using exported name 'bar' as identifier for default export
```

Example of **correct** code:
```js
export foo from './foo.js'
```