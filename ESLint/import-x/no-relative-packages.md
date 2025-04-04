Pattern: Relative package import path

Issue: -

## Description

This rule prevents importing packages through relative paths. It's particularly useful in a monorepo setup, where it's possible to import a sibling package using `../package` relative path, while the direct `package` import is the correct approach.

Using package names instead of relative paths for imports between packages creates a more maintainable and clearer dependency structure, especially when packages are published individually.

## Examples

Given the following folder structure:
```
my-project
├── packages
│   ├── foo
│   │   ├── index.js
│   │   └── package.json
│   └── bar
│       ├── index.js
│       └── package.json
└── entry.js
```

Example of **incorrect** code:
```js
// in my-project/packages/foo.js
import bar from '../bar' // Import sibling package using relative path
import entry from '../../entry.js' // Import from parent package using relative path

// in my-project/entry.js
import bar from './packages/bar' // Import child package using relative path
```

Example of **correct** code:
```js
// in my-project/packages/foo.js
import bar from 'bar' // Import sibling package using package name

// in my-project/entry.js
import bar from 'bar' // Import package using package name
```