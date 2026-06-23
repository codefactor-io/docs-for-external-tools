Pattern: Use of Node.js builtin module

Issue: -

## Description

Node.js builtins (e.g. `fs`, `path`, `crypto`) are not available in browsers, so importing them in client bundles causes runtime failures or forces bundlers to inject heavy polyfills/shims.
This increases bundle size, can leak server-only logic to the client, and may hide environment mismatches until production.

## Examples

Example of **incorrect** code:
```javascript
import fs from "fs";
import path from "path";

var fs = require("fs");
var path = require("path");
```

Example of **correct** code:
```javascript
import _ from "lodash";
import foo from "foo";
import foo from "./foo";

var _ = require("lodash");
var foo = require("foo");
var foo = require("./foo");

/* import/no-nodejs-modules: ["error", {"allow": ["path"]}] */
import path from "path";
```
