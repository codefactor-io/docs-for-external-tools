Pattern: Import from restricted module

Issue: -

## Description

Some imports may be unwanted in a project because they're incompatible with the environment, have been deprecated, or conflict with project standards. For example, a project might standardize on lodash and want to prevent underscore imports, or restrict Node.js-specific modules in browser code.

## Examples

Example of **incorrect** code:
```javascript
import fs from 'fs';  // Node.js module in browser code
import _ from 'underscore';  // Competing with lodash
import { oldMethod } from 'deprecated-lib';
import * as oldStuff from 'legacy-package';

export { something } from 'restricted-package';
```

Example of **correct** code:
```javascript
import _ from 'lodash';  // Preferred utility library
import { readFile } from 'fs/promises';  // If fs is allowed
import { newMethod } from 'modern-lib';

// Using alternatives
import { something } from 'approved-package';
const data = await fetch('/api/data');
```