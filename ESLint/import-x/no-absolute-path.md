Pattern: Absolute path import

Issue: -

## Description

Node.js allows the import of modules using an absolute path such as `/home/xyz/file.js`. This is a bad practice as it ties the code using it to your computer, and therefore makes it unusable in packages distributed on `npm` for instance.

This rule forbids the import of modules using absolute paths, encouraging more portable and reusable code.

## Examples

Example of **incorrect** code:
```js
import f from '/foo'
import f from '/some/path'

var f = require('/foo')
var f = require('/some/path')
```

Example of **correct** code:
```js
import _ from 'lodash'
import foo from 'foo'
import foo from './foo'

var _ = require('lodash')
var foo = require('foo')
var foo = require('./foo')
```

Example of **incorrect** code with `{ commonjs: false, amd: true }`:
```js
define(['/foo'], function (foo) {
  /*...*/
}) // reported

require(['/foo'], function (foo) {
  /*...*/
}) // reported

const foo = require('/foo') // ignored because of explicit `commonjs: false`
```