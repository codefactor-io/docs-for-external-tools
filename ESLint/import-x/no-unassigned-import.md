Pattern: Unassigned module import

Issue: -

## Description

With both CommonJS' `require` and the ES6 modules' `import` syntax, it is possible to import a module but not use its result. This can be done explicitly by not assigning the module to a variable. 

Unassigned imports can indicate either of the following:
- The module is imported but not used
- The module has side-effects (like `should` or CSS imports)

Modules with side-effects make it hard to know whether they are actually used or can be removed. They can also make it harder to test or mock parts of your application.

This rule aims to help identify and reduce modules with side-effects by reporting when a module is imported but not assigned.

## Examples

Example of **incorrect** code:
```js
import 'should'
require('should')

// In <PROJECT_ROOT>/src/app.js
import '../styles/app.css' // Would be incorrect with { "allow": ["styles/*.css"] }
```

Example of **correct** code:
```js
import _ from 'foo'
import _, { foo } from 'foo'
import _, { foo as bar } from 'foo'
import { foo as bar } from 'foo'
import * as _ from 'foo'

const _ = require('foo')
const { foo } = require('foo')
const { foo: bar } = require('foo')
const [a, b] = require('foo')

// Module is not assigned, but it is used
bar(require('foo'))
require('foo').bar
require('foo').bar()
require('foo')()
```

Example of **correct** code with `{ "allow": ["**/*.css", "babel-register"] }`:
```js
import './style.css'
import 'babel-register'

// In <PROJECT_ROOT>/src/app.js with { "allow": ["src/styles/**", "**/scripts/*.js"] }
import './styles/app.css'
import '../scripts/register.js'
```