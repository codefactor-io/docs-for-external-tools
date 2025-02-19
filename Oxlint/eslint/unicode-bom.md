Pattern: Presence of byte order mark (BOM)

Issue: -

## Description

The Unicode Byte Order Mark (BOM) is unnecessary in UTF-8 files, which is the dominant encoding for web content. Since byte ordering doesn't matter when characters are a single byte, including a BOM in UTF-8 files adds unnecessary bytes and can cause issues with some tools.

## Examples

Example of **incorrect** code:
```javascript
﻿// File starts with BOM
const x = 1;
console.log(x);
```

Example of **correct** code:
```javascript
// No BOM at start of file
const x = 1;
console.log(x);

// Or explicit BOM when required
﻿/* eslint unicode-bom: ["error", "always"] */
const x = 1;
```