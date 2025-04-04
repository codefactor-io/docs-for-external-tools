Pattern: Inconsistent export position

Issue: -

## Description

This rule enforces that all exports are declared at the bottom of the file. It will report any export declarations that come before any non-export statements, ensuring better module organization.

## Examples

Example of **incorrect** code:
```js
const bool = true

export default bool

const str = 'foo'
```

```js
export const bool = true

const str = 'foo'
```

Example of **correct** code:
```js
const arr = ['bar']

export const bool = true

export default bool

export function func() {
  console.log('Hello World 🌍')
}

export const str = 'foo'
```