Pattern: Relative parent path import

Issue: -

## Description

This rule prevents imports to folders in relative parent paths (imports using `..` notation). It is useful for enforcing tree-like folder structures instead of complex graph-like folder structures, which can make large, complex codebases easier to maintain.

While this restriction might be a departure from Node's default resolution style, it can help teams avoid debates over "where to put files" and create more maintainable architectures.

To fix violations of this rule, you have three general strategies:
1. Move the file to be in a sibling folder (or higher) of the dependency
2. Pass the dependency as an argument at runtime (dependency injection)
3. Make the dependency a package so it's globally available to all files in your project

## Examples

Given the following folder structure:
```
my-project
├── lib
│   ├── a.js
│   └── b.js
└── main.js
```

Example of **incorrect** code:
```js
// in my-project/lib/a.js
import bar from '../main' // Import parent file using a relative path
```

Example of **correct** code:
```js
// in my-project/main.js
import foo from 'foo' // Import package using module path
import a from './lib/a' // Import child file using relative path

// in my-project/lib/a.js
import b from './b' // Import sibling file using relative path
```