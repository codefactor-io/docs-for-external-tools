Pattern: Unnamed default export

Issue: -

## Description

Ensuring that default exports are named helps improve the grepability of the codebase by encouraging the re-use of the same identifier for the module's default export at its declaration site and at its import sites.

## Examples

Example of **incorrect** code:

```javascript
export default [];
export default () => {};
export default class {}
export default function() {}
export default foo(bar);
export default 123;
export default {};
export default new Foo();
export default `foo`;
export default /^123/;
```

Example of **correct** code:

```javascript
const foo = 123;
export default foo;
export default function foo() {}
export default class MyClass {}
export default function foo() {}
export default foo(bar);
/* eslint import/no-anonymous-default-export: ['error', {"allowLiteral": true}] */
export default 123;
/* eslint import/no-anonymous-default-export: ['error, {"allowArray": true}] */
export default [];
/* eslint import/no-anonymous-default-export: ['error, {"allowArrowFunction": true}] */
export default () => {};
/* eslint import/no-anonymous-default-export: ['error, {"allowAnonymousClass": true}] */
export default class {}
/* eslint import/no-anonymous-default-export: ['error, {"allowAnonymousFunction": true}] */
export default function() {}
/* eslint import/no-anonymous-default-export: ['error, {"allowObject": true}] */
export default {};
/* eslint import/no-anonymous-default-export: ['error, {"allowNew": true}] */
export default new Foo();
/* eslint import/no-anonymous-default-export: ['error, {"allowCallExpression": true}] */
export default foo(bar);
```