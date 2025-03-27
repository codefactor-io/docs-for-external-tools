Pattern: Inconsistent list newline

Issue: -

## Description

Enforce consistent line breaks inside braces of object/array/named imports/exports and function parameters.

Example of **incorrect** code:

```ts
const foo = {
  bar: 'baz', qux: 'quux',
  fez: 'fum'
}
```

Example of **correct** code:

```ts
const foo = {
  bar: 'baz',
  qux: 'quux',
  fez: 'fum'
}

const foo = { bar: 'baz', qux: 'quux', fez: 'fum' }
```