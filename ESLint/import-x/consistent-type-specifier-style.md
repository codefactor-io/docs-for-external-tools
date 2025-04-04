Pattern: Inconsistent type import style

Issue: -

## Description

In both Flow and TypeScript, you can mark an import as a type-only import by adding a "kind" marker to the import. Both languages support two positions for the marker:

**At the top-level**, which marks all names in the import as type-only and applies to named, default, and namespace (for TypeScript) specifiers:

```ts
import type Foo from 'Foo';
import type {Bar} from 'Bar';
// ts only
import type * as Bam from 'Bam';
// flow only
import typeof Baz from 'Baz';
```

**Inline** with the named import, which marks just the specific name in the import as type-only. An inline specifier is only valid for named specifiers, and not for default or namespace specifiers:

```ts
import {type Foo} from 'Foo';
// flow only
import {typeof Bar} from 'Bar';
```

This rule either enforces or bans the use of inline type-only markers for named imports to maintain a consistent style.

## Examples

Example of **incorrect** code with `prefer-top-level` option:
```ts
import {type Foo} from 'Foo';
import Foo, {type Bar} from 'Foo';
// flow only
import {typeof Foo} from 'Foo';
```

Example of **correct** code with `prefer-top-level` option:
```ts
import type {Foo} from 'Foo';
import type Foo, {Bar} from 'Foo';
// flow only
import typeof {Foo} from 'Foo';
```

Example of **incorrect** code with `prefer-inline` option:
```ts
import type {Foo} from 'Foo';
import type Foo, {Bar} from 'Foo';
// flow only
import typeof {Foo} from 'Foo';
```

Example of **correct** code with `prefer-inline` option:
```ts
import {type Foo} from 'Foo';
import Foo, {type Bar} from 'Foo';
// flow only
import {typeof Foo} from 'Foo';
```