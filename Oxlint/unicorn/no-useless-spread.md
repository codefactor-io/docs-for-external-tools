Pattern: Unnecessary spread operator usage

Issue: -

## Description

Many built-in methods and constructs (`Map`, `Set`, `Promise.all`, `for...of`, `yield*`) already accept iterables, making spread syntax unnecessary. Similarly, spreading array or object literals within their own literal type adds no value.

## Examples

Example of **incorrect** code:
```javascript
const array = [firstElement, ...[secondElement], thirdElement];
await Promise.all([...iterable]);
for (const foo of [...set]);
function* foo() {
  yield* [...anotherGenerator()];
}
function foo(bar) {
  return [...bar.map((x) => x * 2)];
}
```

Example of **correct** code:
```javascript
const array = [firstElement, secondElement, thirdElement];
await Promise.all(iterable);
for (const foo of set);
function* foo() {
  yield* anotherGenerator();
}
function foo(bar) {
  return bar.map((x) => x * 2);
}
```