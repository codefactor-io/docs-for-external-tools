Pattern: Dependency cycle

Issue: -

## Description

This rule ensures that there is no resolvable path back to this module via its dependencies. It detects circular dependencies of depth 1 (imported module imports me) up to any depth, if the `maxDepth` option is not set.

Dependency cycles can lead to unexpected behavior as the initialization order becomes ambiguous. This rule does not detect imports that resolve directly to the linted module; for that, see the `no-self-import` rule.

This rule ignores type-only imports in Flow and TypeScript syntax (`import type` and `import typeof`), which have no runtime effect.

## Examples

Example of **incorrect** code:
```js
// dep-b.js
import './dep-a.js'

export function b() {
  /* ... */
}

// dep-a.js
import { b } from './dep-b.js' // Dependency cycle detected
```

Example of **correct** code with `{ maxDepth: 1 }`:
```js
// dep-c.js
import './dep-a.js'

// dep-b.js
import './dep-c.js'

export function b() {
  /* ... */
}

// dep-a.js
import { b } from './dep-b.js' // Not reported as the cycle is at depth 2
```

Example of **correct** code with `{ ignoreExternal: true }`:
```js
// dep-a.js
import 'module-b/dep-b.js'

export function a() {
  /* ... */
}

// node_modules/module-b/dep-b.js
import { a } from './dep-a.js' // Not reported as this module is external
```