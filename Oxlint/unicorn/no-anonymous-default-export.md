Pattern: Anonymous default export

Issue: -

## Description

Using anonymous functions or classes as default exports makes code harder to search and maintain. Named exports ensure consistent identifier use across the codebase, both at declaration and import sites.

## Examples

Example of **incorrect** code:
```javascript
export default class {}
export default function () {}
export default () => {};
module.exports = class {};
```

Example of **correct** code:
```javascript
export default class Foo {}
export default function foo() {}

const foo = () => {};
export default foo;

module.exports = class Foo {};
```