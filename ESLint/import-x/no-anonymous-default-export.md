Pattern: Anonymous default export

Issue: -

## Description

This rule reports if a module's default export is unnamed. This includes several types of unnamed data types: literals, object expressions, arrays, anonymous functions, arrow functions, and anonymous class declarations.

Ensuring that default exports are named helps improve the grepability of the codebase by encouraging the re-use of the same identifier for the module's default export at its declaration site and at its import sites.

## Examples

Example of **incorrect** code:
```js
export default []

export default () => {}

export default class {}

export default function () {}

export default 123

export default {}

export default new Foo()
```

Example of **correct** code:
```js
const foo = 123
export default foo

export default class MyClass() {}

export default function foo() {}
```

Example of **correct** code with `{ "allowArray": true }`:
```js
export default []
```

Example of **correct** code with `{ "allowArrowFunction": true }`:
```js
export default () => {}
```

Example of **correct** code with `{ "allowAnonymousClass": true }`:
```js
export default class {}
```

Example of **correct** code with `{ "allowAnonymousFunction": true }`:
```js
export default function () {}
```

Example of **correct** code with `{ "allowCallExpression": true }`:
```js
export default foo(bar)
```

Example of **correct** code with `{ "allowLiteral": true }`:
```js
export default 123
```

Example of **correct** code with `{ "allowObject": true }`:
```js
export default {}
```

Example of **correct** code with `{ "allowNew": true }`:
```js
export default new Foo()
```