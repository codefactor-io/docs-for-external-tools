Pattern: Missing or inconsistent curly braces

Issue: -

## Description

Require curly braces for nested or multiline control-flow bodies. Multiline conditions in `if`, `while`, and `do...while` statements also require braces. If any branch in an `if`/`else if`/`else` chain uses or requires braces, all branches must use them.

Both braced and unbraced single-line bodies are allowed. This rule is not configurable.

Example of **incorrect** code:

```javascript
if (true)
  console.log({
    foo
  })

if (true)
  if (false) console.log('bar')
```

Example of **correct** code:

```javascript
if (true) {
  console.log({
    foo
  })
}

if (true) {
  if (false) console.log('bar')
}

if (true)
  console.log('hello')

if (true) {
  console.log('hello')
}
```

## Further Reading

* [Antfu - curly](https://github.com/antfu/eslint-plugin-antfu/blob/main/src/rules/curly.md)
* [Antfu - curly tests](https://github.com/antfu/eslint-plugin-antfu/blob/main/src/rules/curly.test.ts)
