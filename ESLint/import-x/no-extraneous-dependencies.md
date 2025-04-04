Pattern: Extraneous dependency import

Issue: -

## Description

This rule forbids the import of external modules that are not declared in the `package.json`'s `dependencies`, `devDependencies`, `optionalDependencies`, `peerDependencies`, or `bundledDependencies`. The closest parent `package.json` will be used. If no `package.json` is found, the rule will not lint anything.

This behavior can be changed with the rule option `packageDir`. The rule normally ignores imports of modules marked internal, but this can be changed with the rule option `includeInternal`. Type imports can be verified by specifying `includeTypes`.

Modules have to be installed for this rule to work.

## Examples

Given the following `package.json`:
```json
{
  "name": "my-project",
  "dependencies": {
    "lodash.find": "^4.2.0"
  },
  "devDependencies": {
    "ava": "^0.13.0"
  },
  "optionalDependencies": {
    "lodash.isarray": "^4.0.0"
  },
  "peerDependencies": {
    "react": ">=15.0.0 <16.0.0"
  },
  "bundledDependencies": ["@generated/foo"]
}
```

Example of **incorrect** code:
```js
// Importing a package not listed in dependencies
var _ = require('lodash');
import _ from 'lodash';

// Importing a devDependency with devDependencies: false option
/* eslint import-x/no-extraneous-dependencies: ["error", {"devDependencies": false}] */
import test from 'ava';
var test = require('ava');

// Importing an optionalDependency with optionalDependencies: false option
/* eslint import-x/no-extraneous-dependencies: ["error", {"optionalDependencies": false}] */
import isArray from 'lodash.isarray';

// Importing an internal module with includeInternal: true option
/* eslint import-x/no-extraneous-dependencies: ["error", {"includeInternal": true}] */
import foo from './foo';

// Importing a type with includeTypes: true option
/* eslint import-x/no-extraneous-dependencies: ["error", {"includeTypes": true}] */
import type { MyType } from 'foo';
```

Example of **correct** code:
```js
// Builtin and internal modules are fine by default
var path = require('path');
var foo = require('./foo');

// Listed in various dependency types
import find from 'lodash.find';
import test from 'ava';
import isArray from 'lodash.isarray';
import foo from '@generated/foo';

// Peer dependencies with peerDependencies: true option
/* eslint import-x/no-extraneous-dependencies: ["error", {"peerDependencies": true}] */
import react from 'react';

// Type imports are ignored by default
import type { MyType } from 'foo';
```