Pattern: Namespace import

Issue: -

## Description

This rule enforces a convention of not using namespace (a.k.a. "wildcard" `*`) imports. Using specific named imports instead of namespace imports can lead to more readable and maintainable code by making dependencies explicit.

The rule is auto-fixable when the namespace object is only used for direct member access, e.g. `namespace.a`.

## Examples

Example of **incorrect** code:
```js
import * as foo from 'foo'
```

```js
import defaultExport, * as foo from 'foo'
```

Example of **correct** code:
```js
import defaultExport from './foo'
import { a, b } from './bar'
import defaultExport, { a, b } from './foobar'
```

Example of **correct** code with `{ "ignore": ["*.ext"] }`:
```js
import * as bar from './ignored-module.ext'
```