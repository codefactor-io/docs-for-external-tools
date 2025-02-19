Pattern: Multiple import statements from same module

Issue: -

## Description

Using multiple import statements from the same module reduces code clarity. Consolidating imports from a module into a single statement makes it easier to see everything being imported from that module at a glance.

## Examples

Example of **incorrect** code:
```javascript
import { merge } from "module";
import something from "another-module";
import { find } from "module";

import { createUser } from './users';
import type { User } from './users';
```

Example of **correct** code:
```javascript
import { merge, find } from "module";
import something from "another-module";

import { createUser, type User } from './users';
```