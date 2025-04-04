Pattern: Mutable export declaration

Issue: -

## Description

This rule forbids the use of mutable exports with `var` or `let`. Mutable bindings can lead to unexpected behavior when importing modules, as changes to these values in the exporting module will also affect the importing modules.

## Examples

Example of **incorrect** code:
```js
export let count = 2
export var count = 3

let count = 4
export { count } // count is mutable because it was declared with let
```

Example of **correct** code:
```js
export const count = 1
export function getCount() {}
export class Counter {}
```

Note that exported function/class declaration identifiers may be reassigned, but are not flagged by this rule at this time. To prevent general reassignment of these identifiers, exported or not, you may want to enable the following core ESLint rules:
- `no-func-assign`
- `no-class-assign`