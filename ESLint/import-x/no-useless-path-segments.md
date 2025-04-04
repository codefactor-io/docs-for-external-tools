Pattern: Unnecessary path segment

Issue: -

## Description

This rule prevents unnecessary path segments in import and require statements. Removing redundant segments makes imports cleaner and easier to understand.

The rule can be configured with the `noUselessIndex` option to also detect unnecessary `/index` or `/index.js` imports in paths, and with the `commonjs` option to check CommonJS imports.

## Examples

Given the following folder structure:
```
my-project
├── app.js
├── footer.js
├── header.js
└── helpers.js
└── helpers
    └── index.js
├── index.js
└── pages
    ├── about.js
    ├── contact.js
    └── index.js
```

Example of **incorrect** code:
```js
// In my-project/app.js
import './../my-project/pages/about.js' // Should be "./pages/about.js"
import './../my-project/pages/about' // Should be "./pages/about"
import '../my-project/pages/about.js' // Should be "./pages/about.js"
import '../my-project/pages/about' // Should be "./pages/about"
import './pages//about' // Should be "./pages/about"
import './pages/' // Should be "./pages"
import './pages/index' // Should be "./pages" (except if there is a ./pages.js file)
import './pages/index.js' // Should be "./pages" (except if there is a ./pages.js file)
```

Example of **correct** code:
```js
// In my-project/app.js
import './header.js'
import './pages'
import './pages/about'
import '.'
import '..'
import fs from 'fs'
```

Example of **incorrect** code with `{ "noUselessIndex": true }`:
```js
// In my-project/app.js
import './helpers/index' // Should be "./helpers/"
import './pages/index' // Should be "./pages"
import './pages/index.js' // Should be "./pages"
```