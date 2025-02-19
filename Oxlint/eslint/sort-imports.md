Pattern: Unsorted import declarations

Issue: -

## Description

Import declarations should be sorted first by the import type (default, namespace, named) and then alphabetically within each group. This makes imports easier to scan and helps developers quickly find specific imports.

## Examples

Example of **incorrect** code:
```javascript
import { c, a, b } from 'foo';
import { x } from 'baz';
import * as helper from 'lib';
import def from 'bar';

import {
  zebra,
  apple,
  banana
} from 'animals';
```

Example of **correct** code:
```javascript
import def from 'bar';
import * as helper from 'lib';
import { a, b, c } from 'foo';
import { x } from 'baz';

import {
  apple,
  banana,
  zebra
} from 'animals';
```