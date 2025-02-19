Pattern: Assignment to imported binding

Issue: -

## Description

ES Modules create read-only bindings. Attempting to reassign imported values, modify imported objects, or extend imported namespaces will cause runtime errors. Use local variables instead if you need to modify imported values.

## Examples

Example of **incorrect** code:
```javascript
import mod, { named } from "./mod.mjs";
import * as ns from "./mod.mjs";

mod = 1;
named = 2;
ns.prop = 3;
ns = {};

Object.assign(ns, { foo: "bar" });
```

Example of **correct** code:
```javascript
import mod, { named } from "./mod.mjs";
import * as ns from "./mod.mjs";

const localMod = mod;
let localNamed = named;
const localNs = { ...ns };

localMod = 1;
localNamed = 2;
localNs.prop = 3;
```