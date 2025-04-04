Pattern: AMD module syntax

Issue: -

## Description

This rule reports `require([array], ...)` and `define([array], ...)` function calls at the module scope. It will not report if there are not exactly 2 arguments, or if the first argument is not a literal array.

The rule is intended for temporary use when migrating from AMD modules to pure ES6 modules.

## Examples

Example of **incorrect** code:
```js
define(['a', 'b'], function (a, b) {
  /* ... */
})

require(['b', 'c'], function (b, c) {
  /* ... */
})
```

Example of **correct** code:
```js
// CommonJS require is still valid
const a = require('a');
const b = require('b');

// ES6 imports
import a from 'a';
import b from 'b';
```