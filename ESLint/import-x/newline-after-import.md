Pattern: Missing newline after import

Issue: -

## Description

This rule enforces having one or more empty lines after the last top-level import statement or require call. This improves readability by clearly separating import statements from the rest of the code.

## Examples

Example of **incorrect** code:
```js
import * as foo from 'foo'
const FOO = 'BAR'
```

```js
import * as foo from 'foo'
const FOO = 'BAR'

import { bar } from 'bar-lib'
```

```js
const FOO = require('./foo')
const BAZ = 1
const BAR = require('./bar')
```

Example of **correct** code:
```js
import defaultExport from './foo'

const FOO = 'BAR'
```

```js
import defaultExport from './foo'
import { bar } from 'bar-lib'

const FOO = 'BAR'
```

```js
const FOO = require('./foo')
const BAR = require('./bar')

const BAZ = 1
```

Example of **incorrect** code with `{ "count": 2, "exactCount": true }`:
```js
import defaultExport from './foo'

const FOO = 'BAR'
```

Example of **correct** code with `{ "count": 2, "exactCount": true }`:
```js
import defaultExport from './foo'


const FOO = 'BAR'
```

Example of **incorrect** code with `{ "considerComments": true }`:
```js
import defaultExport from './foo'
// some comment here.
const FOO = 'BAR'
```

Example of **correct** code with `{ "considerComments": true }`:
```js
import defaultExport from './foo'

// some comment here.
const FOO = 'BAR'
```