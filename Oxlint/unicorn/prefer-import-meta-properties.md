Pattern: Missing use of `import.meta.{dirname,filename}`

Issue: -

## Description

Starting with Node.js 20.11, `import.meta.dirname` and `import.meta.filename` have been introduced in ES modules. 

`import.meta.filename` is equivalent to `url.fileURLToPath(import.meta.url)`. 
`import.meta.dirname` is equivalent to `path.dirname(import.meta.filename)`. 

This rule replaces legacy patterns with `import.meta.dirname` and `import.meta.filename`.

## Examples

Example of **incorrect** code:

```ts
import path from "node:path";
import { fileURLToPath } from "url";

const filename = fileURLToPath(import.meta.url);
const dirname = path.dirname(fileURLToPath(import.meta.url));
const dirname = path.dirname(import.meta.filename);
const dirname = fileURLToPath(new URL(".", import.meta.url));
```

Example of **correct** code:

```ts
const filename = import.meta.filename;
const dirname = import.meta.dirname;
```