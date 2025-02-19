Pattern: New operator with require

Issue: -

## Description

Using new with require is confusing since require doesn't always return a constructor. Import the module first, then create new instances from the imported constructor.

## Examples

Example of **incorrect** code:
```javascript
const header = new require('header');
const db = new require('./database.js');
```

Example of **correct** code:
```javascript
const Header = require('header');
const header = new Header();

const Database = require('./database.js');
const db = new Database();
```