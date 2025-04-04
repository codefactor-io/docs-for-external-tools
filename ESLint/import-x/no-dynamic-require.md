Pattern: Dynamic require statement

Issue: -

## Description

The `require` method from CommonJS is used to import modules from different files. Unlike the ES6 `import` syntax, it can be given expressions that will be resolved at runtime. 

While dynamic requires are sometimes necessary and useful, in most cases they should be avoided. Using expressions (for instance, concatenating a path and variable) as the argument makes it harder for tools to perform static code analysis, or to find where in the codebase a module is used.

This rule forbids every call to `require()` that uses expressions for the module name argument.

## Examples

Example of **incorrect** code:
```js
require(name)
require('../' + name)
require(`../${name}`)
require(name())
```

Example of **correct** code:
```js
require('../name')
require(`../name`)
```