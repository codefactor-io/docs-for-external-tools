Pattern: Use of `_`

Issue: -

## Description

There is a long history of using `_` as a prefix or suffix for private members in JavaScript. It is however recommended to use the formal private class feature introduced in ES2022.

## Examples

Example of **incorrect** code:

```ts
let foo_;
const __proto__ = {};
foo._bar();
```

Example of **correct** code:

```ts
const _ = require("underscore");
const obj = _.contains(items, item);
obj.__proto__ = {};
const file = __filename;
function foo(_bar) {}
const bar = { onClick(_bar) {} };
const baz = (_bar) => {};
```