Pattern: Node.js builtin module usage

Issue: -

## Description

This rule forbids the use of Node.js builtin modules. It can be useful for client-side web projects that do not have access to those modules, preventing errors at runtime when Node.js-specific code is executed in a browser environment.

The rule can be configured with an `allow` option to specify certain Node.js modules that are permitted.

## Examples

Example of **incorrect** code:
```js
import fs from 'fs'
import path from 'path'

var fs = require('fs')
var path = require('path')
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

Example of **correct** code with `{ "allow": ["path"] }`:
```js
import path from 'path'
var path = require('path')
```