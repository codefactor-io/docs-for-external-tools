Pattern: Default export renamed on import

Issue: -

## Description

This rule prohibits importing a default export by another name. This helps maintain consistent naming across the codebase and makes it easier to track the usage of default exports.

Default exports have a clear intended name, and importing them with a different name can create confusion or make the code harder to understand.

## Examples

Given a module file `api/get-users.js`:
```js
export default async function getUsers() {}
```

Example of **incorrect** code:
```js
// Importing getUsers as findUsers
import findUsers from './get-users'
```

Example of **correct** code:
```js
import getUsers from './api/get-users.js'
```