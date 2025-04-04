Pattern: Deprecated rule usage

Issue: -

## Description

This rule was **deprecated** in eslint-plugin-import v2.0.0. Please use the corresponding rule `first` instead.

## Examples

Example of **incorrect** code:
```js
// Using the deprecated rule
// "import-x/imports-first": "error"
```

Example of **correct** code:
```js
// Using the replacement rule
// "import-x/first": "error"
```