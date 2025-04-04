Pattern: Undeclared export reference

Issue: -

## Description

This rule verifies that all named imports are part of the set of named exports in the referenced module. For `export`, it verifies that all named exports exist in the referenced module.

The plugin will find exported names from `module` (or the deprecated `jsnext:main`), if present in `package.json`. A module path that is ignored or not unambiguously an ES module will not be reported when imported. Type imports and exports, as used by Flow, are always ignored.

## Examples

Given a module file `./foo.js`:
```js
export const foo = "I'm so foo"
```

Example of **incorrect** code:
```js
// Importing a name that doesn't exist
import { notFoo } from './foo'

// Re-exporting a name that doesn't exist
export { notFoo as defNotBar } from './foo'

// Following 'jsnext:main', if available
import { dontCreateStore } from 'redux'
```

Example of **correct** code:
```js
// Importing an existing named export
import { foo } from './foo'

// Re-exporting an existing named export
export { foo as bar } from './foo'

// Node modules without module/jsnext:main are not analyzed by default
import { SomeNonsenseThatDoesntExist } from 'react'
```