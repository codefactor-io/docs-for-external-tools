Pattern: Use of CommonJS `require` imports

Issue: -

## Description

Using `require()` for imports instead of ES modules (`import`) reduces code analyzability, makes tree-shaking more difficult, and can lead to harder-to-detect runtime errors. ES modules provide better static analysis and optimization opportunities.

## Examples

Example of **incorrect** code:
```ts
const lib1 = require("lib1");
const { lib2 } = require("lib2");
import lib3 = require("lib3");
```

Example of **correct** code:
```ts
import * as lib1 from "lib1";
import { lib2 } from "lib2";
import * as lib3 from "lib3";
```