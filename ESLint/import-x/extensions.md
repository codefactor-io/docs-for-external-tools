Pattern: Inconsistent file extension usage

Issue: -

## Description

Some file resolve algorithms allow you to omit the file extension within the import source path. In order to provide a consistent use of file extensions across your code base, this rule can enforce or disallow the use of certain file extensions.

This rule can be configured to either enforce extensions for all import statements, forbid them entirely, or selectively enforce them based on file type or package imports.

## Examples

Example of **incorrect** code when configuration set to `"never"`:
```js
import foo from './foo.js'
import bar from './bar.json'
import Component from './Component.jsx'
import express from 'express/index.js'
```

Example of **correct** code when configuration set to `"never"`:
```js
import foo from './foo'
import bar from './bar'
import Component from './Component'
import express from 'express/index'
import * as path from 'path'
```

Example of **incorrect** code when configuration set to `"always"`:
```js
import foo from './foo'
import bar from './bar'
import Component from './Component'
import foo from '@/foo'
```

Example of **correct** code when configuration set to `"always"`:
```js
import foo from './foo.js'
import bar from './bar.json'
import Component from './Component.jsx'
import * as path from 'path'
import foo from '@/foo.js'
```

Example of **incorrect** code when configuration set to `"ignorePackages"`:
```js
import foo from './foo'
import bar from './bar'
import Component from './Component'
```

Example of **correct** code when configuration set to `"ignorePackages"`:
```js
import foo from './foo.js'
import bar from './bar.json'
import Component from './Component.jsx'
import express from 'express'
import foo from '@/foo'
```