Pattern: Unused module or export

Issue: -

## Description

This rule reports:
- Modules without any exports
- Individual exports not being statically imported or required from other modules in the same project
- Dynamic imports are supported if the argument is a literal string

At least one of the options `missingExports` or `unusedExports` must be enabled for this rule to work. The rule can be configured with several options to customize its behavior.

## Examples

Example of **incorrect** code when `missingExports` is enabled:
```js
const class MyClass { /*...*/ }

function makeClass() { return new MyClass(...arguments) }
```

Example of **correct** code when `missingExports` is enabled:
```js
export default function () {
  /*...*/
}

export const foo = function () {
  /*...*/
}

export { foo, bar }

export { foo as bar }
```

Example of **incorrect** code when `unusedExports` is enabled:
```js
// file-a.js
export const a = 1 // Will be reported as unused

// file-d.js
export const i1 = 9 // Will be reported as unused
export default () => {} // Will be reported as unused in file-c

// file-f.js
export { default, i0 } from 'file-d' // Both will be reported
export const j = 99 // Will be reported as unused
```

Example of **correct** code when `unusedExports` is enabled:
```js
// file-a.js
export const b = 2 // Used in file-b
export const c = 3 // Used in file-b
export const d = 4
export { d as e } // Used in file-f
export function doAnything() {} // Used in file-b
export default 5 // Used in file-b

// file-b.js
export const f = 6 // Used in file-f

// file-c.js
export const h = 8 // Used via namespace import in file-f

// file-d.js
export const i0 = 9 // Used in file-f
export default () => {} // Used in file-f
```

Example of **correct** code when `ignoreUnusedTypeExports` is enabled:
```ts
export type Foo = {}; // Will not be reported
export interface Foo = {}; // Will not be reported
export enum Foo {}; // Will not be reported
```