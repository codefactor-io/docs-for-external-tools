Pattern: Duplicate export

Issue: -

## Description

Reports duplicate exports of names or defaults. Repeated exports can lead to ambiguous behavior and are often the result of errors during refactoring, copy/paste operations, or code duplication with an intent to rename.

## Examples

Example of **incorrect** code:
```js
export default class MyClass { /*...*/ } // Multiple default exports.

function makeClass() { return new MyClass(...arguments) }

export default makeClass // Multiple default exports.
```

Example of **incorrect** code:
```js
export const foo = function () {
  /*...*/
} // Multiple exports of name 'foo'.

function bar() {
  /*...*/
}
export { bar as foo } // Multiple exports of name 'foo'.
```

In the case of named/default re-export, all `n` re-exports will be reported, as at least `n-1` of them are clearly mistakes, but it is not clear which one (if any) is intended.