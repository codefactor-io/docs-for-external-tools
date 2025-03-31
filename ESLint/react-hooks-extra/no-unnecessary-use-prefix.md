Pattern: Unnecessary `use` prefix

Issue: -

## Description

Enforces that a function with the 'use' prefix should use at least one Hook inside of it.

If your function doesn’t call any Hooks, avoid the `use` prefix. Instead, write it as a regular function without the `use` prefix. 


Example of **incorrect** code:

```js
function useSorted(items) {
  return items.slice().sort();
}
```

Example of **correct** code:

```js
function getSorted(items) {
  return items.slice().sort();
}
```

## Further Reading

* [GitHub - no-unnecessary-use-prefix](https://eslint-react.xyz/docs/rules/hooks-extra-no-unnecessary-use-prefix)