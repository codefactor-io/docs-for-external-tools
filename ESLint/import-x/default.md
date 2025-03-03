Pattern: Missing default export in imported module

Issue: -

## Description

Using a default import requires the imported module to have a default export. This rule reports cases where a module is imported using default import syntax, but the referenced module does not contain a default export.

## Examples

Example of **incorrect** code:
```javascript
// ./bar.js only contains named exports
import bar from './bar'

// ./baz.js uses CommonJS exports
import baz from './baz'
```

Example of **correct** code:
```javascript
// ./foo.js contains a default export
import foo from './foo'

// Ignored modules (like node_modules) won't trigger warnings
import someModule from 'some-module'
```