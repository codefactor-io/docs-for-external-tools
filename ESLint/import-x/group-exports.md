Pattern: Scattered export declarations

Issue: -

## Description

This rule reports when named exports are not grouped together in a single `export` declaration or when multiple assignments to CommonJS `module.exports` or `exports` object are present in a single file.

By requiring a single export declaration, all your exports will remain in one place, making it easier to see what exports a module provides.

## Examples

Example of **incorrect** code:
```js
// Multiple named export statements
export const first = true
export const second = true
```

```js
// Aggregating exports from the same module
export { module1 } from 'module-1'
export { module2 } from 'module-1'
```

```js
// Multiple exports assignments
exports.first = true
exports.second = true
```

```js
// Multiple exports assignments
module.exports = {}
module.exports.first = true
```

```ts
type firstType = boolean
type secondType = any

// Multiple named type export statements
export type { firstType }
export type { secondType }
```

Example of **correct** code:
```js
// A single named export declaration
export const valid = true
```

```js
const first = true
const second = true

// A single named export declaration
export { first, second }
```

```js
// Aggregating exports from different modules
export { default as module1 } from 'module-1'
export { default as module2 } from 'module-2'
```

```js
// A single exports assignment
module.exports = {
  first: true,
  second: true,
}
```

```ts
const first = true
type firstType = boolean

// A single named export declaration (type exports handled separately)
export { first }
export type { firstType }
```