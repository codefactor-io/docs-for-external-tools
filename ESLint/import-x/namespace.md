Pattern: Invalid namespace member reference

Issue: -

## Description

This rule enforces that names exist at the time they are dereferenced when imported as a full namespace. It will report at the import declaration if there are no exported names found, and will report on assignment to a member of an imported namespace.

The rule also reports for computed references (i.e. `foo["bar"]()`) unless configured otherwise. For packages, the plugin will find exported names from `module` or the deprecated `jsnext:main`, if present in `package.json`. A module path that is ignored or not unambiguously an ES module will not be reported when imported.

## Examples

Given a module file `./named-exports.js`:
```js
export const a = 1
const b = 2
export { b }

const c = 3
export { c as d }

export class ExportedClass {}

// ES7
export * as deep from './deep'
```

And a module file `./deep.js`:
```js
export const e = 'MC2'
```

Example of **incorrect** code:
```js
import * as names from './named-exports'

function notGreat() {
  doSomethingWith(names.c) // 'c' not found in imported namespace 'names'

  const { a, b, c } = names // also reported, only for 'c'
}

// Tunnels through re-exported namespaces
function deepTrouble() {
  doSomethingWith(names.deep.f) // 'f' not found in deeply imported namespace 'names.deep'
}
```

Example of **incorrect** code with `{ allowComputed: false }`:
```js
import * as a from './a'

function f(x) {
  return a[x] // Unable to validate computed reference to imported namespace 'a'
}
```

Example of **correct** code:
```js
import * as names from './named-exports'

function great() {
  return names.a + names.b // Both exist in namespace
}

// Tunnels through re-exported namespaces
function deepFine() {
  doSomethingWith(names.deep.e) // 'e' exists in deep namespace
}
```

Example of **correct** code with `{ allowComputed: true }`:
```js
import * as a from './a'

function f(x) {
  return a[x] // Computed references allowed
}
```