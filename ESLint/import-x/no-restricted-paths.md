Pattern: Restricted path import

Issue: -

## Description

This rule allows you to define restricted zones where importing files from specific paths is forbidden. This is useful in projects that contain files meant to be executed in different environments, such as server-specific code and browser-specific code.

For example, in a web application with separate server and client code, you might want to prevent importing server-only files in your client code.

The rule is configured with `zones` that define the target paths where restrictions apply and the paths that are forbidden to import from. Each zone can also have exceptions and custom error messages.

## Examples

Given the following folder structure:
```
my-project
├── client
│   └── foo.js
│   └── baz.js
└── server
    └── bar.js
```

Example of **incorrect** code with `{ "zones": [ { "target": "./client", "from": "./server" } ] }`:
```js
// In my-project/client/foo.js
import bar from '../server/bar' // Importing from a restricted path
```

Example of **correct** code with `{ "zones": [ { "target": "./client", "from": "./server" } ] }`:
```js
// In my-project/client/foo.js
import baz from '../client/baz'
```

Example with exceptions:

Given the following folder structure:
```
my-project
└── server
    ├── one
    │   └── a.js
    │   └── b.js
    └── two
```

Example of **incorrect** code with:
```json
{
  "zones": [
    {
      "target": "./server/one",
      "from": "./server",
      "except": ["./one"]
    }
  ]
}
```

```js
// In my-project/server/one/a.js
import a from '../two/a' // Restricted path
```

Example of **correct** code with the same configuration:
```js
// In my-project/server/one/a.js
import b from './b' // Path is in the exception list
```