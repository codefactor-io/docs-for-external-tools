Pattern: Unnecessary renaming to same name

Issue: -

## Description

Renaming a variable, import, or export to the same name adds unnecessary verbosity to the code. This often occurs during refactoring when renamings are partially removed or from copy-paste errors.

## Examples

Example of **incorrect** code:
```javascript
import { foo as foo } from 'module';
export { bar as bar };

let { prop: prop } = object;
const { first: first, second: second } = data;

function fn({ name: name }) {}

let { ['foo']: foo } = obj;
```

Example of **correct** code:
```javascript
import { foo } from 'module';
export { bar };

let { prop } = object;
const { first, second } = data;

function fn({ name }) {}

// Only rename when actually changing the name
import { foo as renamed } from 'module';
let { prop: newName } = object;
let { ['foo']: localFoo } = obj;
```