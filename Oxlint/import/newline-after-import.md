Pattern: Missing blank line after import

Issue: -

## Description

Without a blank line, import/require declarations blend into the following logic,
which hurts readability and makes changes harder to scan. A blank line clearly
separates dependencies from implementation.

## Examples

Example of **incorrect** code:
```javascript
import * as foo from "foo";
const FOO = "BAR";

import * as foo from "foo";
const FOO = "BAR";

import { bar } from "bar-lib";

const FOO = require("./foo");
const BAZ = 1;
const BAR = require("./bar");
```

Example of **correct** code:
```javascript
import defaultExport from "./foo";

const FOO = "BAR";

import defaultExport from "./foo";
import { bar } from "bar-lib";

const FOO = "BAR";

const FOO = require("./foo");
const BAR = require("./bar");

const BAZ = 1;
```
